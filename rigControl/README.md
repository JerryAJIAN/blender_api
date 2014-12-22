# File contents

* commands.py: Defines the formal, external public API.  No other
  files define the API, asside from CommandListener, which handles
  the polling for command messages, and the publishing of status data.

* CommandSource.py: defines the API for command events. New sources of
  commands should inherit from this class. The ROS node uses this, to
  convert the ROS messages into API calls.

* CommandListener.py: command handler, accepts events from one or
  more command sources, and queues them with blender.

* blenderUI.py: shim to wire up the emotion/gesture selection panel
  in the blender window, to commands.py.  So, when a button is clicked
  in the blender panel, the code here causes the corresponding
  commands.py API call to be called.

* actuators.py handles autonomous functions: breathing, blinking
  eye saccades.  Does NOT use bpy.

* animationManager.py
  uses bpy, accesses bones....

* blenderPlayback.py ... per-frame service
  uses bpy

* blendedNum.py: Implements a numeric object that allow blending and
  smoothing of values