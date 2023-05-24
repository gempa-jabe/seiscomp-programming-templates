# scevent score

## About

A plugin to compute a score for origins and focal mechanism in scevent and
let scevent use the object with the highest score as preferred one.

## Configuration

The SCORE can be used along with other priorities, such as AGENCY or STATUS.
The only difference is that the SCORE evaluation function is not hardcoded
into scevent but must be provided by the user via plugins.

First compile your plugin. The filename could be `evscorexyz.so`. Then load
the plugin into scevent via `scevent.cfg`:

```
plugins = ${plugins}, evscorexyz
```

Next define the score interface name which is defined in your source code,
e.g. `XYZ`, see `REGISTER_ORIGINSCOREPROCESSOR`.

```
eventAssociation.score = XYZ
```

As last step add the SCORE evaluation to the list of priorities:

```
eventAssociation.priorities = AGENCY, STATUS, SCORE
```
