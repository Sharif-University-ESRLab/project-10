# decompiled remote control framework

## summery

### Input

#### Files

+ rc_dump/system/framework/input.jar

#### Code sources

+ classes.dex

#### Counts

+ Classes: 2
+ Methods: 15
+ Fields: 3
+ Instructions: 1024 (units)

#### Decompilation

+ Top level classes: 1
+At process stage: 0 (0.00%)
+ Code generated: 0 (0.00%)

#### Issues

+ Errors: 0
+ Warnings: 0
+ Nodes with errors: 0
+ Nodes with warnings: 0
+ Total nodes with issues: 0
+ Methods with issues: 0
+ Methods success rate: 100.00%

## descriptions

```
sendKeyEvent(int inputSource, int keyCode, boolean longpress):

calls injectKeyEvent and passes a KeyEvent to it.

KeyEvent(long downTime, long eventTime, int action, int code, int repeat, int metaState, int deviceId, int scancode, int flags, int source) 

injectKeyEvent calls android.hardware.input.inputManager.getInstance().injectKeyEvent(keyEvent, mode)
    /**
     * Injects an input event into the event system on behalf of an application.
     * The synchronization mode determines whether the method blocks while waiting for
     * input injection to proceed.
     * <p>
     * Requires {@link android.Manifest.permission.INJECT_EVENTS} to inject into
     * windows that are owned by other applications.
     * </p><p>
     * Make sure you correctly set the event time and input source of the event
     * before calling this method.
     * </p>
     *
     * @param event The event to inject.
     * @param mode The synchronization mode.  One of:
     * {@link #INJECT_INPUT_EVENT_MODE_ASYNC},
     * {@link #INJECT_INPUT_EVENT_MODE_WAIT_FOR_RESULT}, or
     * {@link #INJECT_INPUT_EVENT_MODE_WAIT_FOR_FINISH}.
     * @return True if input event injection succeeded.
     *
     * @hide
     */
    public boolean injectInputEvent(InputEvent event, int mode) {
        if (event == null) {
            throw new IllegalArgumentException("event must not be null");
        }
        if (mode != INJECT_INPUT_EVENT_MODE_ASYNC
                && mode != INJECT_INPUT_EVENT_MODE_WAIT_FOR_FINISH
                && mode != INJECT_INPUT_EVENT_MODE_WAIT_FOR_RESULT) {
            throw new IllegalArgumentException("mode is invalid");
        }
        try {
            return mIm.injectInputEvent(event, mode);
        } catch (RemoteException ex) {
            throw ex.rethrowFromSystemServer();
        }
    }
```
