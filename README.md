# essaimirroir2

Test d'ecriture depuis gitlab
Ceci est un nouveau test pour voir d'ou viens le commit

Error:
[2025-02-28T17:42:04.503+0000] {celery_executor.py:303} ERROR - Error sending Celery task: No master found for 'mymaster' : Redis<ConnectionPool<Connection<host=redis-headless,port=26379,db=0>>> - ConnectionError('Error 111 connecting to redis-headless:26379. Connection refused.')
Celery Task ID: TaskInstanceKey(dag_id='dag_1', task_id='hello_world_group.task_20', run_id='manual__2025-02-28T17:41:30.299932+00:00', try_number=1, map_index=-1)
Traceback (most recent call last):
  File "/usr/local/lib/python3.9/site-packages/kombu/utils/functional.py", line 32, in __call__
    return self.__value__
AttributeError: 'ChannelPromise' object has no attribute '__value__'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/local/lib/python3.9/site-packages/kombu/transport/virtual/base.py", line 951, in create_channel
    return self._avail_channels.pop()
IndexError: pop from empty list

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/local/lib/python3.9/site-packages/kombu/connection.py", line 472, in _reraise_as_library_errors
    yield
  File "/usr/local/lib/python3.9/site-packages/kombu/connection.py", line 459, in _ensure_connection
    return retry_over_time(
  File "/usr/local/lib/python3.9/site-packages/kombu/utils/functional.py", line 318, in retry_over_time
    return fun(*args, **kwargs)
  File "/usr/local/lib/python3.9/site-packages/kombu/connection.py", line 934, in _connection_factory
    self._connection = self._establish_connection()
  File "/usr/local/lib/python3.9/site-packages/kombu/connection.py", line 860, in _establish_connection
    conn = self.transport.establish_connection()
  File "/usr/local/lib/python3.9/site-packages/kombu/transport/virtual/base.py", line 975, in establish_connection
    self._avail_channels.append(self.create_channel(self))
  File "/usr/local/lib/python3.9/site-packages/kombu/transport/virtual/base.py", line 953, in create_channel
    channel = self.Channel(connection)
  File "/usr/local/lib/python3.9/site-packages/kombu/transport/redis.py", line 744, in __init__
    self.client.ping()
  File "/usr/local/lib/python3.9/site-packages/redis/commands/core.py", line 1205, in ping
    return self.execute_command("PING", **kwargs)
  File "/usr/local/lib/python3.9/site-packages/redis/client.py", line 1266, in execute_command
    conn = self.connection or pool.get_connection(command_name, **options)
  File "/usr/local/lib/python3.9/site-packages/redis/connection.py", line 1461, in get_connection
    connection.connect()
  File "/usr/local/lib/python3.9/site-packages/redis/sentinel.py", line 55, in connect
    return self.retry.call_with_retry(self._connect_retry, lambda error: None)
  File "/usr/local/lib/python3.9/site-packages/redis/retry.py", line 51, in call_with_retry
    raise error
  File "/usr/local/lib/python3.9/site-packages/redis/retry.py", line 46, in call_with_retry
    return do()
  File "/usr/local/lib/python3.9/site-packages/redis/sentinel.py", line 45, in _connect_retry
    self.connect_to(self.connection_pool.get_master_address())
  File "/usr/local/lib/python3.9/site-packages/redis/sentinel.py", line 102, in get_master_address
    master_address = self.sentinel_manager.discover_master(self.service_name)
  File "/usr/local/lib/python3.9/site-packages/redis/sentinel.py", line 296, in discover_master
    raise MasterNotFoundError(f"No master found for {service_name!r}{error_info}")
redis.sentinel.MasterNotFoundError: No master found for 'mymaster' : Redis<ConnectionPool<Connection<host=redis-headless,port=26379,db=0>>> - ConnectionError('Error 111 connecting to redis-headless:26379. Connection refused.')

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/usr/local/lib/python3.9/site-packages/airflow/providers/celery/executors/celery_executor_utils.py", line 213, in send_task_to_executor
    result = task_to_run.apply_async(args=[command], queue=queue)
  File "/usr/local/lib/python3.9/site-packages/celery/app/task.py", line 594, in apply_async
    return app.send_task(
  File "/usr/local/lib/python3.9/site-packages/celery/app/base.py", line 799, in send_task
    amqp.send_task_message(P, name, message, **options)
  File "/usr/local/lib/python3.9/site-packages/celery/app/amqp.py", line 518, in send_task_message
    ret = producer.publish(
  File "/usr/local/lib/python3.9/site-packages/kombu/messaging.py", line 186, in publish
    return _publish(
  File "/usr/local/lib/python3.9/site-packages/kombu/connection.py", line 556, in _ensured
    return fun(*args, **kwargs)
  File "/usr/local/lib/python3.9/site-packages/kombu/messaging.py", line 195, in _publish
    channel = self.channel
  File "/usr/local/lib/python3.9/site-packages/kombu/messaging.py", line 218, in _get_channel
    channel = self._channel = channel()
  File "/usr/local/lib/python3.9/site-packages/kombu/utils/functional.py", line 34, in __call__
    value = self.__value__ = self.__contract__()
  File "/usr/local/lib/python3.9/site-packages/kombu/messaging.py", line 234, in <lambda>
    channel = ChannelPromise(lambda: connection.default_channel)
  File "/usr/local/lib/python3.9/site-packages/kombu/connection.py", line 953, in default_channel
    self._ensure_connection(**conn_opts)
  File "/usr/local/lib/python3.9/site-packages/kombu/connection.py", line 459, in _ensure_connection
    return retry_over_time(
  File "/usr/local/lib/python3.9/contextlib.py", line 137, in __exit__
    self.gen.throw(typ, value, traceback)
  File "/usr/local/lib/python3.9/site-packages/kombu/connection.py", line 476, in _reraise_as_library_errors
    raise ConnectionError(str(exc)) from exc
kombu.exceptions.OperationalError: No master found for 'mymaster' : Redis<ConnectionPool<Connection<host=redis-headless,port=26379,db=0>>> - ConnectionError('Error 111 connecting to redis-headless:26379. Connection refused.')




[2025-03-02T17:48:01.344+0000] {scheduler_job_runner.py:733} INFO - TaskInstance Finished: dag_id=dag_1, task_id=hello_world_group.task_17, run_id=manual__2025-03-02T17:47:30.099955+00:00, map_index=-1, run_start_date=None, run_end_date=None, run_duration=None, state=queued, executor_state=failed, try_number=1, max_tries=0, job_id=None, pool=default_pool, queue=default, priority_weight=2, operator=PythonOperator, queued_dttm=2025-03-02 17:47:55.221829+00:00, queued_by_job_id=6898, pid=None
[2025-03-02T17:48:01.345+0000] {task_context_logger.py:91} ERROR - Executor reports task instance <TaskInstance: dag_1.hello_world_group.task_17 manual__2025-03-02T17:47:30.099955+00:00 [queued]> finished (failed) although the task says it's queued. (Info: None) Was the task killed externally?
Changing /home/airflow/logs/dag_id=dag_1/run_id=manual__2025-03-02T17:47:30.099955+00:00/task_id=hello_world_group.task_17 permission to 509
[2025-03-02T17:48:01.355+0000] {base.py:83} INFO - Using connection ID 'rp_sg_s3_log_conn_dev' for task execution.
[2025-03-02T17:48:01.356+0000] {connection_wrapper.py:382} INFO - AWS Connection (conn_id='rp_sg_s3_log_conn_dev', conn_type='aws') credentials retrieved from login and password.
[2025-03-02T17:48:01.580+0000] {taskinstance.py:2730} ERROR - Executor reports task instance <TaskInstance: dag_1.hello_world_group.task_17 manual__2025-03-02T17:47:30.099955+00:00 [queued]> finished (failed) although the task says it's queued. (Info: None) Was the task killed externally?
