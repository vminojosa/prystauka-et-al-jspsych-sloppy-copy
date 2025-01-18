# prystauka-et-al-jspsych-sloppy-copy
Rough remake of prystauka et al (2023) experimental protocol, using jsPsych

<!DOCTYPE html>
<html>
<head>
    <title>Lexical Interference & Semantic Constraint</title>
    <script src="https://unpkg.com/jspsych@8.2.0"></script>
    <script src="https://unpkg.com/@jspsych/plugin-vsl-grid-scene"></script>
    <script src="https://unpkg.com/@jspsych/plugin-html-keyboard-response"></script>
    <script src="https://unpkg.com/@jspsych/plugin-audio-keyboard-response"></script>
    <script src="https://unpkg.com/@jspsych/extension-webgazer"></script>
    <script src="https://unpkg.com/@jspsych/plugin-preload"></script>
    <link href="https://unpkg.com/jspsych@8.2.0/css/jspsych.css" rel="stylesheet" type="text/css" />
</head>
<body></body>
<script>
    var jsPsych = initJsPsych({
        override_safe_mode: true,
        on_finish: function() {
            jsPsych.data.displayData();
        }
    });

    var timeline = [];

    var welcome = {
        type: jsPsychHtmlKeyboardResponse,
        stimulus: "Welcome to the experiment. Press any key to begin."
    };

    var test = {
        type: jsPsychAudioKeyboardResponse,
        stimulus: 'audio/ringtone.mp3',
        prompt: `
            <table>
                <tr>
                    <td><img src='img/orange.png'></img></td>
                    <td><img src='img/blue.png'></img></td>
                </tr>
                <tr>
                    <td><img src='img/blue.png'></img></td>
                    <td><img src='img/orange.png'></img></td>
                </tr>
            </table>`,
        trial_duration: 2000
    };

    timeline.push(welcome, test);

    jsPsych.run(timeline)

</script>
</html>
