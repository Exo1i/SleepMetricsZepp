# SleepMetricsZepp - Analyzing Sleep Metrics of Amazfit Watches: Uncovering some ambiguity.

"Hello Amazfit Users! Recently, as I was tinkering with my Amazfit GTS 2 Mini and how its data syncs through the app, I stumbled upon some intriguing findings regarding sleep data. Check out this [repository](https://github.com/micw/hacking-mifit-api/tree/master) to find how you can get your sleep data. The sleep data is returned by huami's server as follows: 'slp': {'st': 1692823260, 'ed': 1692856620, 'obt': -24, 'ebt': 537, 'dp': 94, 'lt': 440, 'wk': 22, 'usrSt': -1440, 'usrEd': -1440, 'wc': 1, 'supNap': True, 'supRem': False, 'is': 5, 'lb': 0, 'to': 0, 'dt': 0, 'rhr': 0, 'ss': 87, 'stage': ... [sleep stages]

I've found these refrences inside the zepp app:

- AWAKE_COUNT = "wc"
- AWAKE_MINUTES = "wk"
- DEEP_MINUTES = "dp"
- DREAM_TIME = "dt"
- END_DATE = "ed"
- INTO_SLEEP_COUNT = "is"
- LAZY_BED_COUNT = "lb"
- LIGHT_MINUTES = "lt"
- OFF_BED_DATE = "ebt"
- ON_BED_DATE = "obt"
- REST_HEART_RATE = "rhr"
- SLEEP_FEELING = "sf"
- SLEEP_INFO = "slp"
- SLEEP_ODD_STAGE = "odd_stage"
- SLEEP_POS_ON_BACK = "spob"
- SLEEP_POS_ON_LEFT = "spol"
- SLEEP_POS_ON_RIGHT = "spor"
- SLEEP_POS_ON_STOMACH = "spos"
- SLEEP_SCORE = "ss"
- SLEEP_STAGE = "stage"
- START_DATE = "st"
- SUPPORT_NAP = "supNap"
- SUPPORT_REM = "supRem"
- TURN_OVER_COUNT = "to"
- USER_SLEEP_END = "usrEd"
- USER_SLEEP_START = "usrSt"

Here are some assumptions:
- AWAKE_COUNT ("wc"): This represents the count of awakenings during sleep. It indicates how many times the user woke up from sleep throughout the night.
- AWAKE_MINUTES ("wk"): This represents the total duration, in minutes, spent awake during the sleep cycle. It indicates the total time spent awake during the entire sleep period.
- DEEP_MINUTES ("dp"): This variable refers to the amount of time, in minutes, spent in deep sleep.
- DREAM_TIME ("dt"): This refers to rem stage time span.
- END_DATE ("ed"): This is the timestamp indicating when the sleep period ended.
- INTO_SLEEP_COUNT ("is"): I think this refers to the time spent on bed before falling asleep.
- LAZY_BED_COUNT ("lb"): I don't have any idea what this refers too.
- LIGHT_MINUTES ("lt"): This represents the amount of time, in minutes, spent in the light sleep stage.
- OFF_BED_DATE ("ebt"):I assume that this is the timestamp indicating when the user got out of bed but i can't verify that.
- ON_BED_DATE ("obt"):I assume that this is the timestamp indicating when the user got into bed but I can't also verify that.
- REST_HEART_RATE ("rhr"): This refers to the average resting heart rate during sleep. I think it's 0 in my sleep data as it may (or may not) be related to assisted sleep monitoring.
- SLEEP_FEELING ("sf"): This variable might represent how the user felt about their sleep quality. I think it's related to the "Wake-up mood" in the sleep tab in zepp app.
- SLEEP_INFO ("slp"): Self-explanatory, containg all sleep metrics.
- SLEEP_ODD_STAGE ("odd_stage"): This could potentially refer to any unusual or unexpected sleep stages or patterns observed during the sleep cycle and my sleep data didn't contain this data.
- SLEEP_POS_ON_BACK ("spob"), SLEEP_POS_ON_LEFT ("spol"), SLEEP_POS_ON_RIGHT ("spor"), SLEEP_POS_ON_STOMACH ("spos"): These variables might indicate the amount of time spent sleeping in different positions—on their back, left side, right side, or stomach but my sleep data didn't contain any of them.
- SLEEP_SCORE ("ss"): This variable represents the overall sleep score.
- SLEEP_STAGE ("stage"): This represents the specific sleep stages the user went through during the sleep cycle, such as deep sleep, light sleep, and REM sleep and each stage's beggining and end is also writen `[{'start': 1421, 'stop': 1434, 'mode': 4}, {'start': 1435, 'stop': 1449, 'mode': 5}, {'start': 1450, 'stop': 1492, 'mode': 4}, {'start': 1493, 'stop': 1514, 'mode': 7}` where mode 4 is light sleep, mode 5 is deep sleep stage, mode 7 is awake stage,but i can't yet confirm the mode of rem stage as I didn't record it.
- START_DATE ("st"): This is the timestamp indicating when the sleep period started.
- SUPPORT_NAP ("supNap"), SUPPORT_REM ("supRem"): I think that these variables indicate whether my watch is tracking naps and REM (dreaming) sleep, and i confirm that my watch wasnt recorind rem sleep as i had assisted sleep monitoring off .
- TURN_OVER_COUNT ("to"): This refers to the count of times the person turned over while in bed during the sleep period.
- USER_SLEEP_END ("usrEd") and USER_SLEEP_START ("usrSt"): Idk really, they are just negative numbers.

