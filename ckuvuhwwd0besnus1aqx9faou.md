## Been playing around with DoWhy 0.6 for a day

 [DoWhy](https://github.com/microsoft/dowhy) 's 0.6 release removed 
```
LINE 80: self._graph = self.add_unobserved_common_cause(observed_node_names)
``` 
from its ```dowhy/causal_graph.py```. This means all the wrong "Unobserved Confounders" will be added to the corresponding node categories (i.e., "effect_modifiers") with zero tolerance, which is the expected behaviour.

I know this cuz I've been comparing v0.5.1 with the latest release for a whole day and found that I made a mistake in my DAG...

Anyway. 

