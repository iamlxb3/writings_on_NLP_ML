```python
# init (hyper)-parameters
masking_rate_mul_ratio = 1.1
dicard_loss = 0.05
eval_discard_step = 32
min_task_num = 2
is_discard = True
is_pre_train_finished = False

# init task pool
task_pool = [task_1, ..., task_n]
for task_i in task_pool: # init masking rate for each task
  task_i.masking_highest_rate = rate_high_i
  task_i.masking_rate = rate_low_i

# multi-view pre-training with Curriculum Learning
while not is_pre_train_finished:
	result = pre_train_on_taskes(task_pool, eval_discard_step)
  
  for task_i in task_pool:
    # adjust masking rate loss is going down steadily for each task
    if task_i.mask_rate > masking_lowest_rate:
      if task_i.is_loss_going_down():
        task_i.mask_rate *= masking_rate_mul_ratio
        
    # discard task if it is too easy after reaching its highest masking rate
    if is_discard and len(task_pool) > min_task_num::
      if task_i.too_easy(dicard_loss):
        task_pool.remove(task_i)
```

