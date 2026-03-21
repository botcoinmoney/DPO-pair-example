An example of the current working version (subject to change) of DPO training pairs produced by the BOTCOIN mining system. 
 
 
 Each file is a fully self-contained HF training row containing:

  ┌─────────────────────────────────────┬──────────────────────────────────────────────────────────────────────────────────────┐
  │                Field                │                                       Content                                        │
  ├─────────────────────────────────────┼──────────────────────────────────────────────────────────────────────────────────────┤
  │ document                            │ Full ~22K char numbered prose document (what the miner saw)                          │
  ├─────────────────────────────────────┼──────────────────────────────────────────────────────────────────────────────────────┤
  │ questions                           │ All 10 questions                                                                     │
  ├─────────────────────────────────────┼──────────────────────────────────────────────────────────────────────────────────────┤
  │ constraints                         │ All 9 constraint descriptions                                                        │
  ├─────────────────────────────────────┼──────────────────────────────────────────────────────────────────────────────────────┤
  │ trap_metadata                       │ Trap details (entity, attribute, wrong/correct values)                               │
  ├─────────────────────────────────────┼──────────────────────────────────────────────────────────────────────────────────────┤
  │ prompt                              │ Ready-to-use model input (document + questions + constraints)                        │
  ├─────────────────────────────────────┼──────────────────────────────────────────────────────────────────────────────────────┤
  │ rejected / rejected_text            │ Failed attempt: structured + flattened trace + artifact                              │
  ├─────────────────────────────────────┼──────────────────────────────────────────────────────────────────────────────────────┤
  │ chosen / chosen_text                │ Passing attempt: structured + flattened trace + artifact                             │
  ├─────────────────────────────────────┼──────────────────────────────────────────────────────────────────────────────────────┤
  │ rejected_metadata / chosen_metadata │ Full per-attempt annotations (constraints, trace stats, spatial summary, timing)     │
  ├─────────────────────────────────────┼──────────────────────────────────────────────────────────────────────────────────────┤
  │ pair_annotations                    │ Constraint flips, revision time, trace shape deltas, feedback shown between attempts │
  └─────────────────────────────────────┴──────────────────────────────────────────────────────────────────────────────────────┘
