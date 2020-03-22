# C.V. App

#### Tested using Linux. **Might not work as the same with windows.**

Pre-Requisites:
- [ ] [Open V.I.N.O. Toolkit](https://software.intel.com/en-us/openvino-toolkit)
- [ ] [MQTT](http://mqtt.org/)
- [ ] [FFMPEG](https://www.ffmpeg.org/)
- [ ] [Nodejs](https://nodejs.org/en/)

### Running the App

First, get the MQTT broker and UI installed.

- `cd webservice/server`
- `npm install`
- When complete, `cd ../ui`
- And again, `npm install`

You will need *four* separate terminal windows open in order to see the results. The steps
below should be done in a different terminal based on number. You can open a new terminal
in the workspace in the upper left (File>>New>>Terminal).

1. Get the MQTT broker installed and running.
  - `cd webservice/server/node-server`
  - `node ./server.js`
  - You should see a message that `Mosca server started.`.
2. Get the UI Node Server running.
  - `cd webservice/ui`
  - `npm run dev`
  - After a few seconds, you should see `webpack: Compiled successfully.`
3. Start the ffserver
  - `sudo ffserver -f ./ffmpeg/server.conf`
4. Start the actual application. 
  - First, you need to source the environment for OpenVINO *in the new terminal*:
    - `source /opt/intel/openvino/bin/setupvars.sh -pyver 3.5`
  - To run the app, I'll give you two items to pipe in with `ffmpeg` here, with the rest up to you:
    - `-video_size 1280x720`
    - `-i - http://0.0.0.0:3004/fac.ffm`

Your app should begin running, and you should also see the MQTT broker server noting
information getting published.

*Ft.Udacity*.