
<script>
// import {inject} from 'vue';
import * as d3 from 'd3';
// import eventemitter from './eventEmitter';
//import dataexchange from './dataExchange';
let masterscrew1 = "";
let masterscrew2 = "";

let viewsizes = {
   375:11000,
   414:9500,
   390:13300,
}

console.log(viewsizes);

d3.xml("./assets/images/screw2.svg")
  .then(data => {
      masterscrew2 = data;
});    

let mastersvg = "";

let rootcanal1 = ";15;14;13;12;11;21;22;23;24;25;48;45;44;43;42;41;31;32;33;34;35;38;53;52;51;83;82;81;";
let rootcanal2 = ";18;28;47;46;36;37;85;84;";
let rootcanal3 = ";17;27;16;26;38;55;54;";

// let showtooths_permanent = "1;2;3;4;5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;21;22;23;24;25;26;27;28;29;30;31;32;"
// let showtooths_mixed = "1;5;10;15;25;A;F;I;K;";
// let showtooths_primary = "A;B;C;D;E;F;G;H;I;J;K;L;M;N;O;P;Q;R;S;T;"

// let restoration_excluded = "";

let restoration_top_lingual = ";32;31;30;29;T;28;S;27;R;26;Q;25;P;24;O;23;N;22;M;21;L;20;K;19;18;17;";
let restoration_top_buccal = ";1;2;3;4;A;5;B;9;F;10;G;11;H;12;I;14;16;6;C;7;D;8;E;13;J;15;"
let restoration_top_labial = ";9;F;10;G;11;H;6;C"
let restoration_middle_occlusal = ";1;2;3;4;A;5;B;32;31;30;29;T;28;S;21;L;20;K;19;18;17;12;I;14;16;13;J;15;"
let restoration_middle_incisal = "9;F;10;G;11;H;27;R;26;Q;25;P;24;O;23;N;22;M;6;C;7;D;8;E;"
let restoration_bottom_labial = ";27;R;26;Q;25;P;24;O;23;N;22;M;"
let restoration_bottom_palatal = ";1;2;3;4;A;5;B;9;F;10;G;11;H;12;I;14;16;6;C;7;D;8;E;13;J;15;"
let restoration_bottom_buccal = ";32;31;30;29;T;28;S;21;L;20;K;19;18;17;";
let restoration_left_distal = ";1;2;3;4;A;5;B;32;31;30;29;T;28;S;27;R;26;Q;25;P;6;C;7;D;8;E;"
let restoration_right_distal = ";9;F;10;G;11;H;12;I;14;16;24;O;23;N;22;M;21;L;20;K;19;18;17;13;J;15;"
let restoration_left_mesial = ";9;F;10;G;11;H;12;I;14;16;24;O;23;N;22;M;21;L;20;K;19;18;17;16;13;J;15;"
let restoration_right_mesial = ";1;2;3;4;A;5;B;32;31;30;29;T;28;S;27;R;26;Q;25;P;6;C;7;D;8;E;";
let selectedID = "";
// let swaps ="5||B;6||C"
// let swapbboxadjust = "-4;0;0;0#0;0;0;0#-5;0;0;0||0;0;0;0#0;0;0;0#0;0;0;0"
let startX = 0;
let startY = 0;
let bbox1 = null;
let endY = 0;
let endX = 0;
let bbox2 = null;
let newy = 0;
let y = 0;
let rightX1 = 0;
let x1 = 0;
let x2 = 0;
let y1 = 0;
let y2 = 0;
let eheight = 0;
let bottomcenter = 0;
let r = 0;
let ry = 0;
let hg1 = 0;
let bbox = null;
let x = 0;
let ewidth = 0;
let topcenter = 0;
let cy = 0;
let newx = 0;
let rx = 0;
let cx = 0;
let tidright = 0;
let tidleft = 0;
let tidcenter = 0;
let width = 0;
let height = 0;
let bbox1a = null;
let tkey = null;
let tskey = null;
let idental = 0;
let path1 = '';
let path2 = '';
let path3 = '';
let path = '';
let step1 = false;
let step2 = false;
let step3 = false;
let step4 = false;
let step5 = false;
let step6 = false;
let dentaldata = {};
let ndentaldata = {};
let tsskey = null;
let childkey = null;
let tid1 = null;
let selectedtooth = {} ;
let iopers = null;
let operates = null;
let teethfound = false;
let iteeth = 0;
let includes = {};
let ioper = null;
let width1 = 0;
let height1 = 0;
let wdiff = 0;
let dentaldatafound = false;
let centerY = null;
let circleradius = null;
let centerX = null;
let middlefound = false;
let leftcenter = 0;
let hgt = 0;
let fteeth = null;
let nselectedtooth = {};
let rightcenter = null;
let skey = null;
let sk = null;
let leftfound = null;
let bottomfound = null;
let rightY1 = null;
let rightY3 = null;
let leftX4 = null;

let topfound = null;
let rightfound = null;
let centre = null;
let rotate = null;
let leftX2 = null;
let path4 = null;
let rightX3 = null;
let bbox2a = null;
let bboxa = null;
let bbox3 = null;
let points = [];
let line = null;

let adjustdiagrams = {
     "11":{
         "screw":{x:-245,y:0,width:0,height:0,scalex:1.6,scaley:1,sx:21,sy:25,ssx:-.1,ssy:-.2},
         "drifting":{x:930,y:-50,width:10,height:0,scalex:.5,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
         "sealant":{x:1745,y:360,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},
         "watched":{x:1750,y:355,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
     },      
     "12":{
         "screw":{x:10,y:0,width:0,height:0,scalex:1.3,scaley:1,sx:68.5,sy:23,ssx:-.2,ssy:-.2},
         "drifting":{x:215,y:-45,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
         "sealant":{x:1600,y:350,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},
         "watched":{x:1600,y:350,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},       
     },
     "13":{
         "screw":{x:0,y:0,width:0,height:0,scalex:1.3,scaley:1,sx:67,sy:23,ssx:-.2,ssy:-.2},
         "drifting":{x:5,y:-45,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
         "sealant":{x:1475,y:350,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},
         "watched":{x:1475,y:350,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},
     },   
     "14":{
         "screw":{x:-70,y:0,width:0,height:0,scalex:1.4,scaley:1,sx:57,sy:24,ssx:-.2,ssy:-.2},
         "drifting":{x:-205,y:-40,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
         "sealant":{x:1335,y:350,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},
         "watched":{x:1335,y:350,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},
     },    
     "15":{
         "screw":{x:0,y:0,width:0,height:0,scalex:1.3,scaley:1,sx:55.5,sy:24,ssx:-.2,ssy:-.2},
         "drifting":{x:-405,y:-40,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
         "sealant":{x:1195,y:350,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
         "watched":{x:1195,y:350,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
    },    
     "16":{
         "screw":{x:-2,y:-1,width:0,height:9,scalex:1.3,scaley:1,sx:-11,sy:9,ssx:0,ssy:0},
         "drifting":{x:-620,y:-40,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
         "sealant":{x:1045,y:345,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
         "watched":{x:1045,y:345,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
    },     
    "17":{
         "screw":{x:805,y:-5,width:0,height:24,scalex:.6,scaley:1,sx:495,sy:-1,ssx:-.5,ssy:.2},
         "drifting":{x:-850,y:-30,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
         "sealant":{x:880,y:360,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},
         "watched":{x:880,y:360,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},
    },
    "18":{
        "screw":{x:660,y:-10,width:0,height:37,scalex:.6,scaley:1,sx:409,sy:-13,ssx:-.5,ssy:.5},
        "drifting":{x:-1000,y:-120,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:735,y:360,width:0,height:0,scalex:2.5,scaley:2.5,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:735,y:360,width:0,height:0,scalex:2.5,scaley:2.5,sx:0,sy:0,ssx:0,ssy:0},
    },
    "21":{
        "screw":{x:-272,y:0,width:0,height:0,scalex:1.6,scaley:1,sx:-23.3,sy:25,ssx:-0,ssy:-.2},
        "drifting":{x:680,y:-50,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:1930,y:355,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:1930,y:355,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
    },     
    "22":{
        "screw":{x:15,y:0,width:0,height:0,scalex:1.3,scaley:1,sx:13,sy:24,ssx:-.1,ssy:-.2},
        "drifting":{x:585,y:-45,width:10,height:0,scalex:1,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:2055,y:360,width:0,height:0,scalex:2.8,scaley:2.8,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:2055,y:360,width:0,height:0,scalex:2.8,scaley:2.8,sx:0,sy:0,ssx:0,ssy:0},
    }, 
    "23":{
        "screw":{x:767,y:-1,width:0,height:26,scalex:.9,scaley:1,sx:-112,sy:-5,ssx:0,ssy:.3},
        "drifting":{x:805,y:-45,width:10,height:0,scalex:1,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:2185,y:365,width:0,height:0,scalex:2.2,scaley:2.2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:2185,y:365,width:0,height:0,scalex:2.2,scaley:2.2,sx:0,sy:0,ssx:0,ssy:0},
    }, 
    "24":{
        "screw":{x:814,y:-1,width:0,height:26,scalex:.9,scaley:1,sx:-340,sy:-5,ssx:0.2,ssy:.3},
        "drifting":{x:1215,y:-45,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:2315,y:365,width:0,height:0,scalex:2.2,scaley:2.2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:2315,y:365,width:0,height:0,scalex:2.2,scaley:2.2,sx:0,sy:0,ssx:0,ssy:0},
    },  
    "25":{
        "screw":{x:-118,y:2,width:0,height:10,scalex:1.4,scaley:1,sx:-117,sy:10,ssx:0.1,ssy:0},
        "drifting":{x:1435,y:-45,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:2455,y:360,width:0,height:0,scalex:2.2,scaley:2.2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:2455,y:360,width:0,height:0,scalex:2.2,scaley:2.2,sx:0,sy:0,ssx:0,ssy:0},
    },  
    "26":{
        "screw":{x:17,y:-1,width:0,height:11,scalex:1.3,scaley:1,sx:-61,sy:10,ssx:0,ssy:0},
        "drifting":{x:1745,y:170,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:2605,y:365,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:2605,y:365,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
    }, 
    "27":{
        "screw":{x:2526,y:-6,width:0,height:24,scalex:.6,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "drifting":{x:1985,y:180,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:2775,y:370,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:2775,y:370,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
    },    
    "28":{
        "screw":{x:2669,y:-2,width:0,height:28,scalex:.6,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "drifting":{x:2200,y:-35,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:2930,y:380,width:0,height:0,scalex:1.5,scaley:1.5,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:2930,y:380,width:0,height:0,scalex:1.5,scaley:1.5,sx:0,sy:0,ssx:0,ssy:0},
    },     
    "41":{
        "screw":{x:1564,y:515,width:30,height:0,scalex:.6,scaley:.6,sx:-1026.5,sy:-472,ssx:.8,ssy:0.93},   
        "drifting":{x:490,y:265,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},     
        "sealant":{x:1740,y:790,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},  
        "watched":{x:1740,y:790,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},   
    },  
    "42":{
        "screw":{x:1443,y:505,width:30,height:0,scalex:.6,scaley:.6,sx:-945,sy:-454,ssx:.8,ssy:0.90},   
        "drifting":{x:425,y:265,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0}, 
        "sealant":{x:1605,y:785,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},   
        "watched":{x:1600,y:785,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},   
    },
    "43":{
        "screw":{x:980,y:295,width:0,height:0,scalex:.7,scaley:.7,sx:-660.5,sy:-342,ssx:.7,ssy:0.82}, 
        "drifting":{x:375,y:260,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},    
        "sealant":{x:1480,y:780,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},  
        "watched":{x:1480,y:780,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},         
    },
    "44":{
        "screw":{x:890,y:290,width:0,height:0,scalex:.7,scaley:.7,sx:-597.5,sy:-342,ssx:.7,ssy:0.82},   
        "drifting":{x:315,y:255,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},       
        "sealant":{x:1335,y:780,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0}, 
        "watched":{x:1330,y:780,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0}, 
    },
    "45":{
        "screw":{x:1085,y:514,width:0,height:0,scalex:.6,scaley:.6,sx:-532,sy:-340,ssx:.5,ssy:0.67},     
        "drifting":{x:240,y:255,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},   
        "sealant":{x:1190,y:780,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:1185,y:780,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0}, 
    },
    "46":{
        "screw":{x:1810,y:815,width:0,height:0,scalex:.4,scaley:.5,sx:-570,sy:-406,ssx:.3,ssy:0.64},   
        "drifting":{x:180,y:255,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},   
        "sealant":{x:1040,y:780,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},  
        "watched":{x:1035,y:780,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0}, 
    },
    "47":{
        "screw":{x:1550,y:806,width:0,height:0,scalex:.4,scaley:.5,sx:-484,sy:-446,ssx:.3,ssy:0.7},   
        "drifting":{x:80,y:225,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},     
        "sealant":{x:880,y:780,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:875,y:780,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},
    },
    "48":{
        "screw":{x:1290,y:806,width:0,height:0,scalex:.4,scaley:.5,sx:-400,sy:-510,ssx:.3,ssy:0.8},    
        "drifting":{x:0,y:225,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},    
        "sealant":{x:725,y:780,width:0,height:0,scalex:2.5,scaley:2.5,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:725,y:780,width:0,height:0,scalex:2.5,scaley:2.5,sx:0,sy:0,ssx:0,ssy:0},
    },
    "31":{
        "screw":{x:1740,y:525,width:30,height:0,scalex:.6,scaley:.6,sx:-964.2,sy:-479,ssx:.6,ssy:0.93},   
        "drifting":{x:605,y:265,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},  
        "sealant":{x:1930,y:790,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},      
        "watched":{x:1925,y:790,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},
    },  
    "32":{
        "screw":{x:1860,y:525,width:30,height:0,scalex:.6,scaley:.6,sx:-1030,sy:-478,ssx:.6,ssy:0.93}, 
        "drifting":{x:665,y:265,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},      
        "sealant":{x:2060,y:795,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},   
        "watched":{x:2055,y:795,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},    
    },     
    "33":{
        "screw":{x:2724,y:842,width:30,height:0,scalex:.5,scaley:.5,sx:-1383.5,sy:-602,ssx:.6,ssy:0.93}, 
        "drifting":{x:740,y:255,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},     
        "sealant":{x:2195,y:800,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},     
        "watched":{x:2190,y:800,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},   
    },  
    "34":{
        "screw":{x:2095,y:510,width:30,height:0,scalex:.6,scaley:.6,sx:-1372.5,sy:-483,ssx:.8,ssy:0.95},  
        "drifting":{x:785,y:255,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},      
        "sealant":{x:2320,y:795,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},  
        "watched":{x:2315,y:795,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0}, 
    },      
    "35":{
        "screw":{x:3034,y:510,width:30,height:0,scalex:.5,scaley:.6,sx:-1545,sy:-545,ssx:.6,ssy:1.1},   
        "drifting":{x:855,y:255,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},    
        "sealant":{x:2455,y:790,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},   
        "watched":{x:2450,y:790,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},
    },  
    "36":{
        "screw":{x:6730,y:1290,width:30,height:80,scalex:.3,scaley:.4,sx:2,sy:-601,ssx:-.1,ssy:.7}, 
        "drifting":{x:910,y:255,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},   
        "sealant":{x:2605,y:785,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},      
        "watched":{x:2605,y:785,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},  
    },       
    "37":{
        "screw":{x:7190,y:1290,width:30,height:90,scalex:.3,scaley:.4,sx:2,sy:-602.4,ssx:-.1,ssy:.7}, 
        "drifting":{x:960,y:255,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},     
        "sealant":{x:2775,y:785,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},  
        "watched":{x:2775,y:785,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},  
    }, 
    "38":{
        "screw":{x:7570,y:1310,width:30,height:80,scalex:.3,scaley:.4,sx:2,sy:-602.4,ssx:-.1,ssy:.7},   
        "drifting":{x:990,y:245,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},     
        "sealant":{x:2930,y:785,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0}, 
        "watched":{x:2930,y:785,width:0,height:0,scalex:3,scaley:3,sx:0,sy:0,ssx:0,ssy:0},  
    },       
    "55":{
        "screw":{x:0,y:1,width:0,height:9,scalex:1.3,scaley:1,sx:-15.5,sy:11,ssx:0,ssy:0},
        "drifting":{x:135,y:-820,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:1165,y:365,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:1165,y:365,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
    },  
    "54":{
        "screw":{x:3,y:1,width:0,height:9,scalex:1.3,scaley:1,sx:-20,sy:11,ssx:0,ssy:0},
        "drifting":{x:275,y:-820,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:1305,y:365,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:1305,y:365,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
    },
    "53":{
        "screw":{x:341,y:3,width:0,height:9,scalex:1,scaley:1,sx:262.5,sy:11,ssx:-.4,ssy:0},
        "drifting":{x:350,y:-840,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:1457,y:355,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:1457,y:355,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
    },
    "52":{
        "screw":{x:379,y:1,width:0,height:9,scalex:1,scaley:1,sx:285,sy:9,ssx:-.4,ssy:0},
        "drifting":{x:405,y:-840,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:1585,y:350,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:1585,y:350,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
    },
    "51":{
        "screw":{x:414,y:-20,width:0,height:9,scalex:1,scaley:1,sx:314,sy:9,ssx:-.4,ssy:0},
        "drifting":{x:498,y:-850,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:1745,y:355,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:1745,y:355,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
    },
    "85":{
        "screw":{x:2032,y:806,width:0,height:0,scalex:.4,scaley:.5,sx:-638,sy:-510,ssx:.3,ssy:0.8},    
        "drifting":{x:200,y:-420,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:1155,y:780,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:1155,y:780,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
    },
    "84":{
        "screw":{x:2300,y:820,width:0,height:0,scalex:.4,scaley:.5,sx:-723,sy:-516,ssx:.3,ssy:1},    
        "drifting":{x:285,y:-420,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:1320,y:785,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:1320,y:785,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
    },   
    "83":{
        "screw":{x:2556,y:544,width:0,height:0,scalex:.4,scaley:.6,sx:-457.5,sy:-168,ssx:.1,ssy:0.4},    
        "drifting":{x:350,y:-410,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:1465,y:785,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:1465,y:785,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "rootcanal" :{x:0,y:305,width:0,height:0,scalex:1,scaley:1,sx:0,sy:0,ssx:0,ssy:0}
    },  
    "82":{
        "screw":{x:2754,y:556,width:0,height:0,scalex:.4,scaley:.6,sx:-493.5,sy:-168,ssx:.1,ssy:0.4},    
        "drifting":{x:375,y:-410,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:1580,y:780,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:1580,y:780,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "rootcanal" :{x:0,y:305,width:0,height:0,scalex:1,scaley:1,sx:0,sy:0,ssx:0,ssy:0}
    },     
    "81":{
        "screw":{x:3047,y:566,width:0,height:0,scalex:.4,scaley:.6,sx:-547.5,sy:-172,ssx:.1,ssy:0.4},    
        "drifting":{x:421,y:-402,width:10,height:0,scalex:.8,scaley:1,sx:0,sy:0,ssx:0,ssy:0},
        "sealant":{x:1747,y:788,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "watched":{x:1747,y:788,width:0,height:0,scalex:2,scaley:2,sx:0,sy:0,ssx:0,ssy:0},
        "rootcanal" :{x:0,y:305,width:0,height:0,scalex:1,scaley:1,sx:0,sy:0,ssx:0,ssy:0}
    },     
}


//let screwadjust = {11:{},12:{},13:{},14:{},15:{},16:{},17:{},18:{},21:{},22:{},23:{},24:{},25:{},26:{},27:{},28:{}}


export default { name : "Drawing-Board",
// methods: {
 getadjust:function(group,tid){
   return adjustdiagrams[tid][group];
 }, 
 drawapply: function(operation,tid,category,surface,material,treatment,treatmenttype,status,mstatus){
   console.log(material);
   console.log(treatmenttype);
   console.log(status);
   console.log(mstatus);
   selectedtooth["t_"+tid] = "done";
   let parent = document.querySelector('[rel="'+parseInt(tid)+'T"]').parentNode;
   parent.querySelector('[rel="'+parseInt(tid)+'"]').style.display = "block"; 
   if (parent.querySelectorAll('[rel="'+parseInt(tid)+'"]')[1]){
       parent.querySelectorAll('[rel="'+parseInt(tid)+'"]')[1].style.display = "block";  
   }     
//   d3.select('[tid="t_'+tid+'"]').attr("stroke","green");
//   d3.select('[tid="t_'+tid+'"]').attr("fill","green");
   if (category){
       if (dentaldata[category]){
           if (category.toUpperCase() == "RESTORATION"){
               if (dentaldata[category][surface]){
                   operates = operation.split(";;");
                   for (iopers = 0; iopers < operates.length; iopers++){
                        if (!operates[iopers]){
                            continue;
                        } 
                        if (!dentaldata[category][surface][operates[iopers]]){
                            dentaldata[category][surface][operates[iopers]] = [];
                        } 
                        dentaldata[category][surface][operates[iopers]].push(tid); 
                   }      
               }else{
                   dentaldata[category][surface] = {};
                   operates = operation.split(";;");
                   for (iopers = 0; iopers < operates.length; iopers++){
                        if (!operates[iopers]){
                            continue;
                        } 
                        dentaldata[category][surface][operates[iopers]] = [];
                        dentaldata[category][surface][operates[iopers]].push(tid); 
                   }      
               }   
           }else{  
              if (dentaldata[category][operation]){
                  teethfound = false;
                  for (iteeth = 0; iteeth < dentaldata[category][operation].length; iteeth++){
                       if (dentaldata[category][operation][iteeth] == tid){
                           teethfound = true;
                           break;
                       }
                  } 
                  if (!teethfound){
                      dentaldata[category][operation].push(tid);
                  }       
              }else{
                  dentaldata[category][operation] = [];
                  dentaldata[category][operation].push(tid);
              } 
           }  
       }else{
           if (category.toUpperCase() == "RESTORATION"){
               dentaldata[category] = {};
               if (dentaldata[category][surface]){
                   operates = operation.split(";;");
                   for (iopers = 0; iopers < operates.length; iopers++){
                        if (!operates[iopers]){
                            continue;
                        } 
                        if (!dentaldata[category][surface][operates[iopers]]){
                            dentaldata[category][surface][operates[iopers]] = [];
                        } 
                        dentaldata[category][surface][operates[iopers]].push(tid); 
                   }      

               }else{
                   dentaldata[category][surface] = {};
                   operates = operation.split(";;");
                   for (iopers = 0; iopers < operates.length; iopers++){
                        if (!operates[iopers]){
                            continue;
                        } 
                        if (!dentaldata[category][surface][operates[iopers]]){
                             dentaldata[category][surface][operates[iopers]] = [];
                        }
                        dentaldata[category][surface][operates[iopers]].push(tid); 
                   }      
               }   
           }else{   
              if (category != "REST"){ 
                  dentaldata[category] = {};
                  dentaldata[category][operation] = [];    
                  dentaldata[category][operation].push(tid);
              }  
           }   
       }
   }else{
       if (category != "REST"){ 
           if (!dentaldata[operation]){ 
               dentaldata[operation] = [];
               dentaldata[operation].push(tid);
           }else{
               teethfound = false;
               for (iteeth = 0; iteeth < dentaldata[operation].length; iteeth++){
                    if (dentaldata[operation][iteeth] == tid){
                        teethfound = true;
                        break;
                    }
               } 
               if (!teethfound){
                   dentaldata[operation].push(tid);
               }
           }     
       }    
   }
   if (includes[category]){
       if (includes[category][surface]){
           for (ioper = 0; ioper < includes[category][surface].length; ioper++){
                if (operation.toUpperCase().indexOf(";;"+includes[category][surface][ioper].name.toUpperCase()+";;") > -1){
                    includes[category][surface][ioper].included = false;   
                }
           } 
       }  
   }
   // generatedatafordbupdate();
   if (operation.toUpperCase() == "TOOTHROOT"){
       let linecolor = "red";
       mstatus.forEach((stat)=>{
           if (stat.name.toUpperCase() === status.toUpperCase()){
               linecolor = stat.color;
           }
       });
       d3.selectAll("#drawing_"+tid).remove();
       if (rootcanal1.indexOf(";"+tid+";") > -1){
           if ((parseInt(tid) > 10 && parseInt(tid) < 19) || (parseInt(tid) > 20 && parseInt(tid) < 29) || (parseInt(tid) > 50 && parseInt(tid) < 54) || (parseInt(tid) > 80 && parseInt(tid) < 84)){
               bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
               bbox2 = d3.select('[rel="'+tid+'A"]').node().getBoundingClientRect();
               startX = bbox1.x + (bbox1.width/2) ;
               endX = (bbox1.x+(bbox1.width/2));
               endY = bbox1.y + .5;
               path= this.interpolateQuadraticBezierCurve(0, 1, startX+1, startY+1, startX-2, startY,endX+1, endY-1);
               if (parseInt(tid) === 15){
                   startY = bbox1.y+(bbox1.height/5)-2;
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-2, startX-2, startY,endX+1, endY);
               }
               if (parseInt(tid) === 14){
                   startY = bbox1.y+(bbox1.height/5)-2;
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+1, startY-2, startX-2, startY,endX, endY);
               }
               if (parseInt(tid) === 13){
                   startY = bbox1.y+(bbox1.height/5)-2;
                   endX += 1;
                   startX -= 5;
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY+1, startX-4, startY,endX+1.5, endY);
               }
               if (parseInt(tid) === 12){
                   startY = bbox1.y+(bbox1.height/5)-2;
                   endX += 7;
                   startX -= 0;                
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+2, startY-1, startX-4, startY,endX+3.5, endY);
               }
               if (parseInt(tid) === 11){
                   startY = bbox1.y+(bbox1.height/5)-2;
                   endX -= 2;
                   startX -= 3;                
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+1, startY-5, startX+4, startY,endX, endY);
               }
               if (parseInt(tid) === 21){
                   startY = bbox1.y+(bbox1.height/5)-2;
                   endX -= 4;
                   startX -= 3;                
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-5, startX+4, startY,endX-1, endY);
               }
               if (parseInt(tid) === 22){
                   startY = bbox1.y+(bbox1.height/5)-1;
                   endX += 7;
                   startX -= 0;                
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+2, startY-1, startX-4, startY,endX+3.5, endY);
               }
               if (parseInt(tid) === 23){
                   startY = bbox1.y+(bbox1.height/5)-2;
                   endX += 1;
                   startX -= 5;
                   startY += 12;
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY+1, startX-4, startY,endX+1.5, endY);
               }
               if (parseInt(tid) === 24){
                   startY = bbox1.y+(bbox1.height/5)-2;
                   endX += 1;
                   startX -= 5;
                   startY += 12;                   
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY+1, startX-4, startY,endX+1.5, endY);
               }
               if (parseInt(tid) === 25){
                   startY = bbox1.y+(bbox1.height/5)-2;
                   endX += 1;
                   startX -= 2;
                   startY += 12;                   
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY+1, startX-4, startY,endX+1.5, endY);
               }
               if (parseInt(tid) === 53){
                   startY = bbox1.y+(bbox1.height/5)+10;
                   endX -= 3;
                   startX -= 8;           
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+2, startY-1, startX-4, startY,endX+3.5, endY);
               }
               if (parseInt(tid) === 52){
                   startY = bbox1.y+(bbox1.height/5)+5;
                   endX += 8;
                   startX += 2;                
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+2, startY-1, startX-4, startY,endX+3.5, endY);
               } 
               if (parseInt(tid) === 51){
                   startY = bbox1.y+(bbox1.height/5)-19;
                   endX -= 9;
                   startX += 2;                
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY-1, startX, startY,endX+3.5, endY);
               }    
               if (parseInt(tid) === 83){
                   startY = bbox1.y+(bbox1.height/5)+19;
                   endX -= 3;
                   startX -= 2;           
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+2, startY-1, startX-4, startY,endX+3.5, endY);
               }
               console.log(tid);
               if (parseInt(tid) === 82){
                   startY = bbox1.y+(bbox1.height/5)+15;
                   endX -= 2;
                   startX -= 1;                
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+2, startY-1, startX-4, startY-10,endX+3.5, endY-5);
               } 
               if (parseInt(tid) === 81){
                   startY = bbox1.y+(bbox1.height/5)+12;
                   endX -= 3;
                   startX += 3;                 
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY-1, startX, startY-20,endX+3.5, endY-9);
               }                                                
               let newpos = this.getadjust("rootcanal",parseInt(tid));
               console.log(newpos);
               let x = 0;
               let y = 10;
               let scalex = 1;
               let scaley = 1;
               if (newpos){
                   x = newpos.x;
                   y = newpos.y;
                   scalex = newpos.scalex;
                   scaley = newpos.scaley
               }    
               console.log(y); 
               d3.select("#"+mastersvg).select("#svg").select("g").append("g").attr("transform","translate("+x+","+y+") scale("+scalex+","+scaley+")").attr("id","drawing_"+tid);         
               d3.select("#drawing_"+tid).append("path").attr("d",path).style("fill","none").style("stroke",linecolor).style("stroke-width","2px");
           }
           if ((parseInt(tid) > 40 && parseInt(tid) < 49) || (parseInt(tid) > 30 && parseInt(tid) < 39)){
               bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
               startX = bbox1.x + (bbox1.width/2) ;
               endX = (bbox1.x+(bbox1.width/2))+12;
               hgt = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
               endY = bbox1.y+bbox1.height;
               if (parseInt(tid) === 48 || parseInt(tid) === 38){  
                   if (parseInt(tid) === 48){ 
                       startY = bbox1.y+bbox1.height-(hgt.height*6); 
                       startY -= 4;
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX+3, startY-10,startX-3, startY,endX+8, endY-1);
                   }else{
                       startY = bbox1.y+bbox1.height-(hgt.height*4)+9;
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX+1, startY-7, startX-10, startY,endX+6, endY-2);
                   }
               }else{
                   startY = bbox1.y+bbox1.height-(hgt.height*6); 
                   startY -= 3;
                   endX -= 5;
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-8, startX-3, startY,endX+1, endY);
                   if (parseInt(tid) === 41){
                       startY += 24;
                       startX -= 0;
                       endX -= 11;                       
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-3, startX-1, startY,endX+1, endY);
                   }        
                   if (parseInt(tid) === 42){
                       startY += 24;
                       startX -= 0;
                       endX -= 8;                          
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-2, startX-3, startY,endX, endY);
                   }        
                   if (parseInt(tid) === 43){
                       startY += 24;
                       startX -= 7;
                       endX -= 15;                      
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX+4, startY-2, startX-2, startY,endX+3, endY-1);
                   }        
                   if (parseInt(tid) === 44){    
                       endX -= 2;              
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX+1, startY-7, startX-2, startY,endX, endY);
                   }        
                   if (parseInt(tid) === 45){
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-3, startX-2, startY,endX-1, endY);
                   }        
                   if (parseInt(tid) === 31){
                       startY += 30;
                       startX += 3;
                       endX -= 5;                        
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX+1, startY-7, startX-2, startY,endX, endY);
                   }        
                   if (parseInt(tid) === 32){
                       startY += 27;
                       startX += 2;
                       endX -= 7;                       
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-8, startX-1, startY,endX, endY);
                   }     
                   if (parseInt(tid) === 33){
                       startY += 39;
                       startX += 8;
                       endX -= 1;                      
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-8, startX-1, startY,endX, endY);
                   }            
                   if (parseInt(tid) === 34){
                       startY -= 5;
                       startX += 2;
                       endX -= 7;                      
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-8, startX-4, startY,endX, endY);
                   }            
                   if (parseInt(tid) === 35){
                       startY += 4;
                       startX += 2;
                       endX -= 4;                                         
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-8, startX-8, startY,endX, endY);
                   }                                                
               } 
               let newpos = this.getadjust("rootcanal",parseInt(tid));
               let x = 0;
               let y = 10;
               let scalex = 1;
               let scaley = 1;
               if (newpos){
                   x = newpos.x;
                   y = newpos.x;
                   scalex = newpos.scalex;
                   scaley = newpos.scaley
               }     
               d3.select('#'+mastersvg).select("#svg").select("g").append("g").attr("transform","translate("+x+","+y+") scale("+scalex+","+scaley+")").attr("id","drawing_"+tid);         
               d3.select("#drawing_"+tid).append("path").attr("d",path).style("fill","none").style("stroke",linecolor).style("stroke-width","2px");                
           }                  
       }    
       if (rootcanal2.indexOf(";"+tid+";") > -1){
           if ((parseInt(tid) > 10 && parseInt(tid) < 19) || (parseInt(tid) > 20 && parseInt(tid) < 29) || (parseInt(tid) > 45 && parseInt(tid) < 49) || (parseInt(tid) > 30 && parseInt(tid) < 39) || (parseInt(tid) > 83 && parseInt(tid) < 86 ) ){
               if (parseInt(tid) === 47 || parseInt(tid) === 37 || parseInt(tid) === 36 || parseInt(tid) === 46 || parseInt(tid) === 84  || parseInt(tid) === 85){
                   bbox1 = d3.select('#'+mastersvg).select('[rel="'+tid+'T"]').node().getBBox();
                   startX = bbox1.x + (bbox1.width/2) ;
                   endX = (bbox1.x+(bbox1.width/2));
                   hgt = d3.select('#'+mastersvg).select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
                   startY = bbox1.y+bbox1.height-(hgt.height * 6.2);
                   endY = bbox1.y+bbox1.height;
                   console.log(hgt);
                   let newpos = this.getadjust("rootcanal",parseInt(tid));
                   let x = 0;
                   let y = 10;
                   let scalex = 1;
                   let scaley = 1;
                   if (newpos){
                       x = newpos.x;
                       y = newpos.x;
                       scalex = newpos.scalex;
                       scaley = newpos.scaley
                   }      
                   if (parseInt(tid) === 47){             
                       path1= this.interpolateQuadraticBezierCurve(0, 1, startX-20, startY-2, startX-35, startY+25,endX+5, endY);
                       path2= this.interpolateQuadraticBezierCurve(0, 1, startX+11, startY-5, startX+31, startY+25,startX+24, endY-2);
                       path3= this.interpolateQuadraticBezierCurve(0, 1, startX-20, startY-2, startX, startY-5,startX+11, startY-5);       
                   }
                   if (parseInt(tid) === 37){             
                       path1= this.interpolateQuadraticBezierCurve(0, 1, startX-10, startY-2, startX-35, startY+25,endX+5, endY);
                       path2= this.interpolateQuadraticBezierCurve(0, 1, startX+10, startY-5, startX+33, startY+25,startX+24, endY-2);
                       path3= this.interpolateQuadraticBezierCurve(0, 1, startX-10, startY-2, startX, startY-5,startX+11, startY-5);       
                   }          
                   if (parseInt(tid) === 36){             
                       path1= this.interpolateQuadraticBezierCurve(0, 1, startX-10, startY-2, startX-35, startY+25,endX-15, endY);
                       path2= this.interpolateQuadraticBezierCurve(0, 1, startX+10, startY-5, startX+33, startY+25,startX+24, endY-2);
                       path3= this.interpolateQuadraticBezierCurve(0, 1, startX-10, startY-2, startX, startY-5,startX+11, startY-5);       
                   }       
                   if (parseInt(tid) === 46){             
                       path1= this.interpolateQuadraticBezierCurve(0, 1, startX-20, startY-2, startX-35, startY+25,endX-27, endY);
                       path2= this.interpolateQuadraticBezierCurve(0, 1, startX+8, startY-5, startX+23, startY+25,startX+11, endY);
                       path3= this.interpolateQuadraticBezierCurve(0, 1, startX-20, startY-3, startX, startY-5,startX+8, startY-4);       
                   }       
                   if (parseInt(tid) === 85){
                       path1= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY-2, startX-25, startY+25,endX+14, endY);
                       path2= this.interpolateQuadraticBezierCurve(0, 1, startX+23, startY-5, startX+36, startY+25,startX+35, endY);
                       path3= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY-3, startX, startY-5,startX+23, startY-4);       
                   }       
                   if (parseInt(tid) === 84){
                       path1= this.interpolateQuadraticBezierCurve(0, 1, startX-15, startY-2, startX-35, startY+25,endX-20, endY);
                       path2= this.interpolateQuadraticBezierCurve(0, 1, startX+10, startY-5, startX+28, startY+25,startX+18, endY);
                       path3= this.interpolateQuadraticBezierCurve(0, 1, startX-15, startY-3, startX, startY-5,startX+8, startY-4);       
                   }                                                      
                   d3.select('#'+mastersvg).select("#svg").select("g").append("g").attr("transform","translate("+x+","+y+") scale("+scalex+","+scaley+")").attr("id","drawing_"+tid);         
                   d3.select('#'+mastersvg).select("#drawing_"+tid).append("path").attr("d",path1).style("fill","none").style("stroke",linecolor);
                   d3.select('#'+mastersvg).select("#drawing_"+tid).append("path").attr("d",path2).style("fill","none").style("stroke",linecolor);
                   d3.select('#'+mastersvg).select("#drawing_"+tid).append("path").attr("d",path3).style("fill","none").style("stroke",linecolor);
               } 
               if (parseInt(tid) === 18 || parseInt(tid) === 28){
                   bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
                   startX = bbox1.x + (bbox1.width/2) ;
                   endX = (bbox1.x+(bbox1.width/2));
                   startY = bbox1.y+(bbox1.height/3);
                   endY = bbox1.y;
                   let newpos = this.getadjust("rootcanal",parseInt(tid));
                   let x = 0;
                   let y = 10;
                   let scalex = 1;
                   let scaley = 1;
                   if (newpos){
                       x = newpos.x;
                       y = newpos.x;
                       scalex = newpos.scalex;
                       scaley = newpos.scaley
                   }                    
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX-8, startY,endX+1, endY-1);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+5, startY+1, startX+8, startY,startX+4, endY-1);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX, startY-3,startX+5, startY+1);
                   if (parseInt(tid) === 18){
                       path1= this.interpolateQuadraticBezierCurve(0, 1, startX-15, startY-25, startX-28, startY-20 ,endX-25, endY+8);
                       path2= this.interpolateQuadraticBezierCurve(0, 1, startX+10, startY-28, startX+25, startY-25,startX-8, endY);
                       path3= this.interpolateQuadraticBezierCurve(0, 1, startX-16, startY-25, startX+5, startY-25,startX+13, startY-28);
                   } 
                   if (parseInt(tid) === 28){
                       path1= this.interpolateQuadraticBezierCurve(0, 1, startX-13, startY-22, startX-28, startY-50,endX+5, endY+1);
                       path2= this.interpolateQuadraticBezierCurve(0, 1, startX+13, startY-27, startX+30, startY-50,startX+15, endY+5);
                       path3= this.interpolateQuadraticBezierCurve(0, 1, startX-13, startY-23, startX+5, startY-35,startX+13, startY-26);
//                       path3= this.interpolateQuadraticBezierCurve(0, 1, startX-16, startY+1, startX, startY+3,startX+10, startY+1);
                    } 
                   d3.select('#'+mastersvg).select("#svg").select("g").append("g").attr("transform","translate("+x+","+y+") scale("+scalex+","+scaley+")").attr("id","drawing_"+tid);         
                   d3.select('#'+mastersvg).select("#drawing_"+tid).append("path").attr("d",path1).style("fill","none").style("stroke",linecolor);
                   d3.select('#'+mastersvg).select("#drawing_"+tid).append("path").attr("d",path2).style("fill","none").style("stroke",linecolor);
                   d3.select('#'+mastersvg).select("#drawing_"+tid).append("path").attr("d",path3).style("fill","none").style("stroke",linecolor);
               }
           }
       }    
       if (rootcanal3.indexOf(";"+tid+";") > -1){
           if ((parseInt(tid) > 10 && parseInt(tid) < 19) || (parseInt(tid) > 20 && parseInt(tid) < 29) || (parseInt(tid) > 50 && parseInt(tid) < 57)){
               bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
               startX = bbox1.x + (bbox1.width/2) ;
               endX = (bbox1.x+(bbox1.width/2));
               startY = bbox1.y+(bbox1.height/3);
               endY = bbox1.y;
               let newpos = this.getadjust("rootcanal",parseInt(tid));
               let x = 0;
               let y = 10;
               let scalex = 1;
               let scaley = 1;
               if (newpos){
                   x = newpos.x;
                   y = newpos.x;
                   scalex = newpos.scalex;
                   scaley = newpos.scaley
               }                
               path1= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX-8, startY,endX+1, endY-1);
               path2= this.interpolateQuadraticBezierCurve(0, 1, startX+5, startY+1, startX+8, startY,startX+4, endY-1);
               path3= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX, startY-3,startX+5, startY+1);
               if (parseInt(tid) === 17  || parseInt(tid) === 27){
                   if (parseInt(tid) === 17){
                       path1= this.interpolateQuadraticBezierCurve(0, 1, startX-9, startY-30, startX-27, startY-55,endX+2, endY+15);
                       path2= this.interpolateQuadraticBezierCurve(0, 1, startX+18, startY-35, startX+30, startY-55,startX+7, endY+20);
                       path3= this.interpolateQuadraticBezierCurve(0, 1, startX-9, startY-29, startX+5, startY-50,startX+19, startY-34);
                       path4= this.interpolateQuadraticBezierCurve(0, 1, startX+4, startY-40, startX, startY-45,endX+6, endY);
                   }   
                   if (parseInt(tid) === 27){
                       path1= this.interpolateQuadraticBezierCurve(0, 1, startX-9, startY-30, startX-27, startY-55,endX+4, endY+10);
                       path2= this.interpolateQuadraticBezierCurve(0, 1, startX+18, startY-28, startX+30, startY-55,startX+9, endY+20);
                       path3= this.interpolateQuadraticBezierCurve(0, 1, startX-9, startY-31, startX+3, startY-45,startX+19, startY-28);
                       path4= this.interpolateQuadraticBezierCurve(0, 1, startX+4, startY-38, startX, startY-60,endX+8, endY);
                   }                       
               } 
               if (parseInt(tid) === 16 || parseInt(tid) === 26){
                   if (parseInt(tid) === 16){
                       path1= this.interpolateQuadraticBezierCurve(0, 1, startX-14, startY-45, startX-35, startY-85,endX-17, endY+5);
                       path2= this.interpolateQuadraticBezierCurve(0, 1, startX+18, startY-40, startX+30, startY-85,startX+23, endY+10);
                       path3= this.interpolateQuadraticBezierCurve(0, 1, startX-15, startY-44, startX+5, startY-55,startX+19, startY-40);
                       path4= this.interpolateQuadraticBezierCurve(0, 1, startX-3, startY-50, startX, startY-45,endX+4, endY);
                   }
                   if (parseInt(tid) === 26){
                       path1= this.interpolateQuadraticBezierCurve(0, 1, startX-14, startY-40, startX-35, startY-85,endX-17, endY+5);
                       path2= this.interpolateQuadraticBezierCurve(0, 1, startX+18, startY-38, startX+30, startY-85,startX+23, endY+10);
                       path3= this.interpolateQuadraticBezierCurve(0, 1, startX-14, startY-40, startX, startY-55,startX+19, startY-38);
                       path4= this.interpolateQuadraticBezierCurve(0, 1, startX-3, startY-47, startX, startY-45,endX+4, endY);
                   }                      
               }     
               if (parseInt(tid) === 55 || parseInt(tid) === 54){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-14, startY-41, startX-35, startY-85,endX-17, endY+5);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+18, startY-41, startX+30, startY-85,startX+23, endY+10);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-15, startY-41, startX, startY-58,startX+19, startY-42);
                   path4= this.interpolateQuadraticBezierCurve(0, 1, startX-3, startY-48, startX, startY-45,endX+4, endY);
               }                         
               d3.select('#'+mastersvg).select("#svg").select("g").append("g").attr("transform","translate("+x+","+y+") scale("+scalex+","+scaley+")").attr("id","drawing_"+tid);         
               d3.select('#'+mastersvg).select("#drawing_"+tid).append("path").attr("d",path1).style("fill","none").style("stroke",linecolor);
               d3.select('#'+mastersvg).select("#drawing_"+tid).append("path").attr("d",path2).style("fill","none").style("stroke",linecolor);
               d3.select('#'+mastersvg).select("#drawing_"+tid).append("path").attr("d",path3).style("fill","none").style("stroke",linecolor);
               d3.select('#'+mastersvg).select("#drawing_"+tid).append("path").attr("d",path4).style("fill","none").style("stroke",linecolor);
           }
       }    
       if (d3.select("#svg").select("g").select("#coverbox")){
           d3.select("#svg").select("g").select("#coverbox").remove();
           selectedID = "";
           window.emitter.emit('selectedTeeth',selectedID)   
       }       
   } 

   if (operation.toUpperCase() == "SCREW"){
       d3.selectAll("#drawing_"+tid).remove();   
       d3.select('[rel="'+tid+'"]').style("display","block"); 
       d3.select("#"+mastersvg).select("#svg").select("g").append("g").attr("id","drawing_"+tid);
       let linecolor = "red";
       mstatus.forEach((stat)=>{
           if (stat.name.toUpperCase() === status.toUpperCase()){
               linecolor = stat.color;
           }
       });    
       if ((parseInt(tid) > 10 && parseInt(tid) < 19) || (parseInt(tid) > 20 && parseInt(tid) < 29)){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           startX = bbox1.x;
           endX = (bbox1.x+bbox1.width);
           endY = bbox1.y+(bbox1.height/4);
           startY = bbox1.y;
           startX -= 25;
           endX += 25;
           width = endX - startX;
           height = endY - startY;
//            startX -= 279;
//            startY -= 10;
            startX -= (startX/4.1);
            let newpos = this.getadjust("screw",parseInt(tid));
            if (newpos){
                startX += newpos.x;
                endX += newpos.x;
                startY += newpos.y;
                endY += newpos.y;                
                width += newpos.width;
                height += newpos.height;
            }     
//            startX = startY - (startY / 1.2);
//           endX = endY - (endY / 1.2);            
//           path1= interpolateQuadraticBezierCurve(0, 1, startX+5, startY-3, startX+10, endY-24,endX-3, startY-2);
//           path2= interpolateQuadraticBezierCurve(0, 1, startX+5, startY-1, startX+4, startY-3,endX-3, startY-1);
//           d3.select("#drawing_"+tid).append("path").attr("d",path1).style("mask","url(#mask-screw-stripe)").style("stroke","red");
//           d3.select("#drawing_"+tid).append("path").attr("d",path2).style("fill","none").style("stroke","red");
             d3.select("#drawing_"+tid).append("image").attr("transform","scale("+newpos.scalex+","+newpos.scaley+")").attr("href","./assets/images/screw1.png").attr("x",startX).attr("y",startY).attr("width",width).attr("height",height);
 //            path1= this.interpolateQuadraticBezierCurve(0, 1, 0, endY, 10, (startY/2),0, startY);
 //            path2= this.interpolateQuadraticBezierCurve(0, 1, startX+11, startY-5, startX+31, startY+25,startX+24, endY-2);
 //            path3= this.interpolateQuadraticBezierCurve(0, 1, startX-20, startY-2, startX, startY-5,startX+11, startY-5);       
 //            d3.select("#drawing_"+tid).append("path").attr("transform","translate("+(startX+300)+","+(startY-200)+")").attr("d",path1).style("fill","none").style("stroke",linecolor);
 //            d3.select("#drawing_"+tid).append("path").attr("d",path2).style("fill","none").style("stroke",linecolor);
//             d3.select("#drawing_"+tid).append("path").attr("d",path3).style("fill","none").style("stroke",linecolor);
           d3.xml("./assets/images/screw1.svg")
             .then(data => {     
                masterscrew1 = data;
     //           console.log(startX);
     //           console.log(newpos.scalex+1.2);
     //           startX = bbox1.x;
     //           console.log(startX-(startX/(newpos.scalex+1.2)));
     //           let newX = startX-(startX/(newpos.scalex+1.2));
     //           newX = newX/1.2;
                d3.select("#drawing_"+tid).append("g");
                let scalex = (newpos.scalex + 1.1)+newpos.ssx;
                let scaley = (newpos.scaley + .8)+newpos.ssy;
                let newX = (startX -(startX/scalex)) + newpos.sx;
                let newY = (startY -(startY/scaley)) + newpos.sy;
   //             newX = newX - (newX/(newpos.scalex+1.2));
   //             newY = newY - (newY/(newpos.scaley+.8));
                d3.select("#drawing_"+tid).select("g").attr("transform","scale("+scalex+","+scaley+") translate("+newX+","+newY+")").node().append(masterscrew1.documentElement)        
                // console.log(d3.select("#drawing_"+tid).select("image").node().getBoundingClientRect());
                d3.select("#drawing_"+tid).select("#masterscrew1").select("g").attr("stroke",linecolor);   
                if (parent.querySelectorAll('[rel="'+parseInt(tid)+'"]')[1]){
                    parent.querySelectorAll('[rel="'+parseInt(tid)+'"]')[1].style.display = "none";
                }else{
                    parent.querySelector('[rel="'+parseInt(tid)+'"]').style.display = "none";                
                }    
           });    
       }  
       if (tid == "A" || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I" || tid == "J"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           startX = bbox1.x  ;
           endX = (bbox1.x+bbox1.width);
           endY = bbox1.y+(bbox1.height/3);
           startY = bbox1.y;
           if (tid == "A"){
               startX = startX+1;
               endX = endX+1;
               startY = startY+3;
               endY = endY+3;
           } 
           if (tid == "B"){
               startX = startX-2;
               endX = endX-2;
           } 
           if (tid == "C"){
               startX = startX-1;
               endX = endX-1;
               startY = startY+2;
               endY = endY+2;
           } 
           if (tid == "D"){
               startX = startX+2;
               endX = endX+2;
               startY = startY+1;
               endY = endY+1;
           } 
           if (tid == "E"){
               startX = startX-1;
               endX = endX-1;
               startY = startY-1;
               endY = endY-1;
           } 
           if (tid == "F"){
               startX = startX-1;
               endX = endX-1;
               startY = startY-1;
               endY = endY-1;
           } 
           if (tid == "G"){
               startX = startX+2;
               endX = endX+2;
           } 
           if (tid == "i"){
               startX = startX-2;
               endX = endX-2;
           } 
//           path1= interpolateQuadraticBezierCurve(0, 1, startX+5, startY-3, startX+10, endY-24,endX-3, startY-2);
//           path2= interpolateQuadraticBezierCurve(0, 1, startX+5, startY-1, startX+4, startY-3,endX-3, startY-1);
//           d3.select("#drawing_"+tid).append("path").attr("d",path1).style("mask","url(#mask-screw-stripe)").style("stroke","red");
//           d3.select("#drawing_"+tid).append("path").attr("d",path2).style("fill","none").style("stroke","red");
          d3.select("#drawing_"+tid).append("image").attr("href","./assets/images/screw1.png").attr("x",startX).attr("y",startY).attr("width",(endX-startX)).attr("height",(endY-startY));
       }  
       if ((parseInt(tid) > 50 && parseInt(tid) < 56) || (parseInt(tid) > 60 && parseInt(tid) < 66)){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           startX = bbox1.x;
           endX = (bbox1.x+bbox1.width);
           endY = bbox1.y+(bbox1.height/4);
           startY = bbox1.y;
           startX -= 25;
           endX += 25;
           width = endX - startX;
           height = endY - startY;
//            startX -= 279;
//            startY -= 10;
            startX -= (startX/4.1);
            let newpos = this.getadjust("screw",parseInt(tid));
            if (newpos){
                startX += newpos.x;
                endX += newpos.x;
                startY += newpos.y;
                endY += newpos.y;                
                width += newpos.width;
                height += newpos.height;
            }     
//            startX = startY - (startY / 1.2);
//           endX = endY - (endY / 1.2);            
//           path1= interpolateQuadraticBezierCurve(0, 1, startX+5, startY-3, startX+10, endY-24,endX-3, startY-2);
//           path2= interpolateQuadraticBezierCurve(0, 1, startX+5, startY-1, startX+4, startY-3,endX-3, startY-1);
//           d3.select("#drawing_"+tid).append("path").attr("d",path1).style("mask","url(#mask-screw-stripe)").style("stroke","red");
//           d3.select("#drawing_"+tid).append("path").attr("d",path2).style("fill","none").style("stroke","red");
             d3.select("#drawing_"+tid).append("image").attr("transform","scale("+newpos.scalex+","+newpos.scaley+")").attr("href","./assets/images/screw1.png").attr("x",startX).attr("y",startY).attr("width",width).attr("height",height);
 //            path1= this.interpolateQuadraticBezierCurve(0, 1, 0, endY, 10, (startY/2),0, startY);
 //            path2= this.interpolateQuadraticBezierCurve(0, 1, startX+11, startY-5, startX+31, startY+25,startX+24, endY-2);
 //            path3= this.interpolateQuadraticBezierCurve(0, 1, startX-20, startY-2, startX, startY-5,startX+11, startY-5);       
 //            d3.select("#drawing_"+tid).append("path").attr("transform","translate("+(startX+300)+","+(startY-200)+")").attr("d",path1).style("fill","none").style("stroke",linecolor);
 //            d3.select("#drawing_"+tid).append("path").attr("d",path2).style("fill","none").style("stroke",linecolor);
//             d3.select("#drawing_"+tid).append("path").attr("d",path3).style("fill","none").style("stroke",linecolor);
           d3.xml("./assets/images/screw1.svg")
             .then(data => {     
                masterscrew1 = data;
     //           console.log(startX);
     //           console.log(newpos.scalex+1.2);
     //           startX = bbox1.x;
     //           console.log(startX-(startX/(newpos.scalex+1.2)));
     //           let newX = startX-(startX/(newpos.scalex+1.2));
     //           newX = newX/1.2;
                d3.select("#drawing_"+tid).append("g");
                let scalex = (newpos.scalex + 1.1)+newpos.ssx;
                let scaley = (newpos.scaley + .8)+newpos.ssy;
                let newX = (startX -(startX/scalex)) + newpos.sx;
                let newY = (startY -(startY/scaley)) + newpos.sy;
   //             newX = newX - (newX/(newpos.scalex+1.2));
   //             newY = newY - (newY/(newpos.scaley+.8));
                d3.select("#drawing_"+tid).select("g").attr("transform","scale("+scalex+","+scaley+") translate("+newX+","+newY+")").node().append(masterscrew1.documentElement)        
                // console.log(d3.select("#drawing_"+tid).select("image").node().getBoundingClientRect());
                d3.select("#drawing_"+tid).select("#masterscrew1").select("g").attr("stroke",linecolor);   
                if (parent.querySelectorAll('[rel="'+parseInt(tid)+'"]')[1]){
                    parent.querySelectorAll('[rel="'+parseInt(tid)+'"]')[1].style.display = "none";
                }else{
                    parent.querySelector('[rel="'+parseInt(tid)+'"]').style.display = "none";                
                }    
           });    
       }
       if ((parseInt(tid) > 80 && parseInt(tid) < 86) || (parseInt(tid) > 70 && parseInt(tid) < 76)){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           startX = bbox1.x;
           endX = bbox1.x+bbox1.width;
           hgt = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
           startY = bbox1.y+bbox1.height-hgt.height-5;
           startX -= 25;
           endX += 25;
           width = endX - startX;
           height = endY - startY;
           startX -= (startX/4.1);
           let newpos = this.getadjust("screw",parseInt(tid));
           console.log(newpos);
           if (newpos){
                startX += newpos.x;
                endX += newpos.x;
                startY += newpos.y;
                endY += newpos.y;                
                width += newpos.width;
                height += newpos.height;
            }              
          d3.select("#drawing_"+tid).append("image").attr("transform","scale("+newpos.scalex+","+newpos.scaley+")").attr("href","./assets/images/screw2.png").attr("x",startX).attr("y",startY).attr("width",width);   // .attr("height",height);
          d3.xml("./assets/images/screw2.svg")
             .then(data => {     
                masterscrew2 = data;
     //           console.log(startX);
     //           console.log(newpos.scalex+1.2);
     //           startX = bbox1.x;
     //           console.log(startX-(startX/(newpos.scalex+1.2)));
     //           let newX = startX-(startX/(newpos.scalex+1.2));
     //           newX = newX/1.2;
                d3.select("#drawing_"+tid).append("g");
                let scalex = (newpos.scalex + 1.1)+newpos.ssx;
                let scaley = (newpos.scaley + .8)+newpos.ssy;
                let newX = (startX -(startX/scalex)) + newpos.sx;
                let newY = (startY -(startY/scaley)) + newpos.sy;
   //             newX = newX - (newX/(newpos.scalex+1.2));
   //             newY = newY - (newY/(newpos.scaley+.8));
                d3.select("#drawing_"+tid).select("g").attr("transform","scale("+scalex+","+scaley+") translate("+newX+","+newY+")").node().append(masterscrew2.documentElement)        
                // console.log(d3.select("#drawing_"+tid).select("image").node().getBoundingClientRect());
                d3.select("#drawing_"+tid).select("#masterscrew2").select("g").attr("stroke",linecolor);
                let parent = document.querySelector('[rel="'+parseInt(tid)+'A"]').parentNode;
                if (parent.querySelectorAll('[rel="'+parseInt(tid)+'"]')[1]){
                    parent.querySelectorAll('[rel="'+parseInt(tid)+'"]')[1].style.display = "none";
                }else{
                    parent.querySelectorAll('[rel="'+parseInt(tid)+'"]')[0].style.display = "none";                
                }    
           });    
       } 
       if ((parseInt(tid) > 40 && parseInt(tid) < 49) || (parseInt(tid) > 30 && parseInt(tid) <  39)){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           startX = bbox1.x;
           endX = bbox1.x+bbox1.width;
           hgt = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
           startY = bbox1.y+bbox1.height-hgt.height-5;
           startX -= 25;
           endX += 25;
           width = endX - startX;
           height = endY - startY;
           startX -= (startX/4.1);
           let newpos = this.getadjust("screw",parseInt(tid));
           console.log(newpos);
           if (newpos){
                startX += newpos.x;
                endX += newpos.x;
                startY += newpos.y;
                endY += newpos.y;                
                width += newpos.width;
                height += newpos.height;
            }              
          d3.select("#drawing_"+tid).append("image").attr("transform","scale("+newpos.scalex+","+newpos.scaley+")").attr("href","./assets/images/screw2.png").attr("x",startX).attr("y",startY).attr("width",width);   // .attr("height",height);
          d3.xml("./assets/images/screw2.svg")
             .then(data => {     
                masterscrew2 = data;
     //           console.log(startX);
     //           console.log(newpos.scalex+1.2);
     //           startX = bbox1.x;
     //           console.log(startX-(startX/(newpos.scalex+1.2)));
     //           let newX = startX-(startX/(newpos.scalex+1.2));
     //           newX = newX/1.2;
                d3.select("#drawing_"+tid).append("g");
                let scalex = (newpos.scalex + 1.1)+newpos.ssx;
                let scaley = (newpos.scaley + .8)+newpos.ssy;
                let newX = (startX -(startX/scalex)) + newpos.sx;
                let newY = (startY -(startY/scaley)) + newpos.sy;
   //             newX = newX - (newX/(newpos.scalex+1.2));
   //             newY = newY - (newY/(newpos.scaley+.8));
                d3.select("#drawing_"+tid).select("g").attr("transform","scale("+scalex+","+scaley+") translate("+newX+","+newY+")").node().append(masterscrew2.documentElement)        
                // console.log(d3.select("#drawing_"+tid).select("image").node().getBoundingClientRect());
                d3.select("#drawing_"+tid).select("#masterscrew2").select("g").attr("stroke",linecolor);
                let parent = document.querySelector('[rel="'+parseInt(tid)+'A"]').parentNode;
                if (parent.querySelectorAll('[rel="'+parseInt(tid)+'"]')[1]){
                    parent.querySelectorAll('[rel="'+parseInt(tid)+'"]')[1].style.display = "none";
                }else{
                    parent.querySelectorAll('[rel="'+parseInt(tid)+'"]')[0].style.display = "none";                
                }    
           });    
       }  
 
   } 
   if (operation.toUpperCase() == "VENEER"){
       d3.select("#svg").append("svg").attr("id","drawing_"+tid).attr("viewBox",d3.select('[rel="'+tid+'A"]').attr("viewBox"))
       d3.select("#drawing_"+tid).append("path").attr("d",d3.select('[rel="'+tid+'A"]').select("path").attr("d")).style("fill","red").style("stroke","red")
   } 
   if (operation.toUpperCase() == "SEALANT"){
       let linecolor = "red";
       mstatus.forEach((stat)=>{
           if (stat.name.toUpperCase() === status.toUpperCase()){
               linecolor = stat.color;
           }
       });
       d3.selectAll("#drawing_"+tid).remove();       
       d3.select("#"+mastersvg).select("#svg").select("g").append("g").attr("id","drawing_"+tid).append("g");
       let newpos = this.getadjust("sealant",parseInt(tid));    
       bbox = d3.select('[rel="'+tid+'B"]').node().getBBox();   
       console.log(bbox);
  //     circleradius = 12;
     
  //     centerX = (circleradius/2);
 //      centerY = (circleradius * 1.3);  
       d3.select("#drawing_"+tid).select("g").attr("transform","translate("+newpos.x+","+newpos.y+") scale("+newpos.scalex+","+newpos.scaley+")").append("text").style("stroke",linecolor).style("stroke-width","2px").style("fill","red").text("S")
 //            .attr("x",centerX)
 //            .attr("y",centerY)
             .attr("font-size",(bbox.width/1.2)+"px")            

   } 
   if (operation.toUpperCase() == "WATCHED"){
       let linecolor = "red";
       mstatus.forEach((stat)=>{
           if (stat.name.toUpperCase() === status.toUpperCase()){
               linecolor = stat.color;
           }
       });    
       d3.selectAll("#drawing_"+tid).remove();     
       d3.select("#"+mastersvg).select("#svg").select("g").append("g").attr("id","drawing_"+tid).append("g");
       let newpos = this.getadjust("watched",parseInt(tid));    
       bbox = d3.select('[rel="'+tid+'B"]').node().getBBox();   
  //     circleradius = 12;
     
  //     centerX = (circleradius/2);
 //      centerY = (circleradius * 1.3);  
       d3.select("#drawing_"+tid).select("g").attr("transform","translate("+newpos.x+","+newpos.y+") scale("+newpos.scalex+","+newpos.scaley+")").append("text").style("stroke",linecolor).style("stroke-width","2px").style("fill","red").text("W")
 //            .attr("x",centerX)
 //            .attr("y",centerY)
             .attr("font-size",(bbox.width/1.5)+"px")            

   } 

   if (operation.toUpperCase() == "WATCHNONE"){
       if (tid < 17){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x = (bbox1.x+(bbox1.width/1.5));
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           centerX = x;
           centerY = y-(bbox2.height/2);
           circleradius = 12;
           centerX = centerX - (circleradius/1.5);
           centerY = centerY + (circleradius/4);
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("text").style("stroke","red").style("fill","none").text("W")
             .attr("x",centerX)
             .attr("y",centerY)
             .attr("font-size",circleradius+"px")
       } 
       if (tid == "A" || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x = (bbox1.x+(bbox1.width/1.5));
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           centerX = x;
           centerY = y-(bbox2.height/2);
           circleradius = 12;
           centerX = centerX - (circleradius/1.5);
           centerY = centerY + (circleradius/4);
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("text").style("stroke","red").style("fill","none").text("W")
             .attr("x",centerX)
             .attr("y",centerY)
             .attr("font-size",circleradius+"px")
       } 
       if (tid > 16){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x = (bbox1.x+(bbox1.width/1.5));
           y = bbox1.y;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           centerX = x;
           centerY = y+(bbox2.height/1.5);
           circleradius = 12;
           centerX = centerX - (circleradius/1.5);
           centerY = centerY + (circleradius/4);
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("text").style("stroke","red").style("fill","none").text("W")
             .attr("x",centerX)
             .attr("y",centerY)
             .attr("font-size",circleradius+"px")
       }
       if (tid == "K" || tid == "L" || tid == "M" || tid == "N" || tid == "O" || tid == "P" || tid == "Q" || tid == "R" || tid == "S" || tid == "T"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x = (bbox1.x+(bbox1.width/1.5));
           y = bbox1.y;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           centerX = x;
           centerY = y+(bbox2.height/1.5);
           circleradius = 12;
           centerX = centerX - (circleradius/1.5);
           centerY = centerY + (circleradius/4);
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("text").style("stroke","red").style("fill","none").text("W")
             .attr("x",centerX)
             .attr("y",centerY)
             .attr("font-size",circleradius+"px")
       }
   } 

   if (operation.toUpperCase() == "CLASS5"){
       if (parseInt(tid) > 0 && parseInt(tid) < 17){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x+bbox1.width - 2; // (bbox1.width/2) ;
           endY = bbox1.y+(bbox1.height/3)+8
           if (tid == 8 || tid == 9 || tid == 10 || tid == 11 || tid == 12 || tid == 13){
               endY = bbox1.y+(bbox1.height/3)+4
           }
           bbox1a = d3.select('[rel="'+tid+'A"]').node().getBBox();
           hg1 = bbox1a.height/3;
           d3.select("#svg").append("g").attr("id","drawing_"+tid)      
           step1=true,step2=true,step3=true,step4=true,step5=true,step6=true;
           if (tid == 2){
               step5 = false;
               step6 = false;
           }        

           if (tid == 3){
               step5 = false;
               step6 = false;
           }        

           if (tid == 4 || tid == 5 || tid == 6 || tid == 7 || tid == 8 || tid == 9 || tid == 11 || tid == 12 || tid == 13 || tid == 14 || tid == 15 || tid == 16){
               step5 = false;
               step6 = false;
           }        


           if (step1){
               d3.select("#drawing_"+tid).append("line").attr("id","1_"+tid).style("stroke","red")
                  .attr("x1",startX)
                  .attr("y1",endY)
                  .attr("x2",startX-4)
                  .attr("y2",endY);                  
           }

           if (step2){   
               d3.select("#drawing_"+tid).append("line").attr("id","2_"+tid).style("stroke","red")
                  .attr("x1",startX-4)
                  .attr("y1",endY)
                  .attr("x2",startX-4)
                  .attr("y2",endY+hg1);                  
           }  

           if (step3){   
               d3.select("#drawing_"+tid).append("line").attr("id","3_"+tid).style("stroke","red")
                 .attr("x1",startX-4)
                 .attr("y1",endY+hg1)
                 .attr("x2",startX-8)
                 .attr("y2",endY+hg1);                  
           }
 
           if (step4){ 
               d3.select("#drawing_"+tid).append("line").attr("id","4_"+tid).style("stroke","red")
                 .attr("x1",startX-8)
                 .attr("y1",endY+hg1)
                 .attr("x2",startX-8)
                 .attr("y2",endY+hg1+hg1);          
           }

           if (step5){  
               d3.select("#drawing_"+tid).append("line").attr("id","3_"+tid).style("stroke","red")
                 .attr("x1",startX-8)
                 .attr("y1",endY+hg1+hg1)
                 .attr("x2",startX-12)
                 .attr("y2",endY+hg1+hg1);                  
           }    

           if (step6){ 
               d3.select("#drawing_"+tid).append("line").attr("id","4_"+tid).style("stroke","red")
                 .attr("x1",startX-12)
                 .attr("y1",endY+hg1+hg1)
                 .attr("x2",startX-12)
                 .attr("y2",endY+hg1+hg1+hg1);  
           } 
       } 

       if (parseInt(tid) > 16 && parseInt(tid) < 33){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           startX = bbox1.x + (bbox1.width/2) ;
           endX = (bbox1.x+bbox1.width);
           hgt = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
           startY = bbox1.y+bbox1.height-hgt.height-20;
//           endY = startY //bbox1.y+bbox1.height;
           endY = startY-2  
           if (tid == 24 || tid == 25 || tid == 27){
               startX = startX+5;
           }    
           if (tid == 20 || tid == 21 || tid == 22 || tid == 23 || tid == 24 || tid == 25 || tid == 26 || tid == 27 || tid == 28 || tid == 29){
               endY = endY - 3;
           }  
           if (tid == 25){
               endY = endY+1;
           }       
           if (tid == 27){
               endY = endY+7;
           }      
           hgt = d3.select('[rel="'+tid+'A"]').node().getBBox();
           hg1 = hgt.height/3;
           step1=true,step2=true,step3=true,step4=true,step5=true,step6=true;
           if (tid == 18){ 
               step6 = false;
           }  
           if (tid == 19){ 
               step6 = false;
           }  

           if (tid == 31){ 
               step6 = false;
           }  

           if (tid == 32){ 
               endY = endY-2
           }  

           if (tid == 20 || tid == 21 || tid == 22 || tid == 23 || tid == 24 || tid == 25 || tid == 26 || tid == 27 || tid == 28 || tid == 29){ 
               step5 = false;
               step6 = false;
           }  


           d3.select("#svg").append("g").attr("id","drawing_"+tid)      
           if (step1){
               d3.select("#drawing_"+tid).append("line").attr("id","1_"+tid).style("stroke","red")
                  .attr("x1",startX)
                  .attr("y1",endY)
                  .attr("x2",startX-4)
                  .attr("y2",endY);                  
           }

           if (step2){   
               d3.select("#drawing_"+tid).append("line").attr("id","2_"+tid).style("stroke","red")
                  .attr("x1",startX-4)
                  .attr("y1",endY)
                  .attr("x2",startX-4)
                  .attr("y2",endY+hg1);                  
           }  

           if (step3){   
               d3.select("#drawing_"+tid).append("line").attr("id","3_"+tid).style("stroke","red")
                 .attr("x1",startX-4)
                 .attr("y1",endY+hg1)
                 .attr("x2",startX-8)
                 .attr("y2",endY+hg1);                  
           }
 
           if (step4){ 
               d3.select("#drawing_"+tid).append("line").attr("id","4_"+tid).style("stroke","red")
                 .attr("x1",startX-8)
                 .attr("y1",endY+hg1)
                 .attr("x2",startX-8)
                 .attr("y2",endY+hg1+hg1);          
           }

           if (step5){  
               d3.select("#drawing_"+tid).append("line").attr("id","3_"+tid).style("stroke","red")
                 .attr("x1",startX-8)
                 .attr("y1",endY+hg1+hg1)
                 .attr("x2",startX-12)
                 .attr("y2",endY+hg1+hg1);                  
           }    

           if (step6){ 
               d3.select("#drawing_"+tid).append("line").attr("id","4_"+tid).style("stroke","red")
                 .attr("x1",startX-12)
                 .attr("y1",endY+hg1+hg1)
                 .attr("x2",startX-12)
                 .attr("y2",endY+hg1+hg1+hg1);  
           } 
       }


       if (tid == "T" || tid == "S" || tid == "R" || tid == "Q" || tid == "P" || tid == "O" || tid == "N" || tid == "M" || tid == "L" || tid == "K"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           startX = bbox1.x + (bbox1.width/2) ;
           endX = (bbox1.x+bbox1.width);
           hgt = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
           startY = bbox1.y+bbox1.height-hgt.height-20;
//           endY = startY //bbox1.y+bbox1.height;
           endY = startY-2  
           if (tid == "R" || tid == 25 || tid == 27){
               startX = startX+5;
           }    
           if (tid == 20 || tid == 21 || tid == 22 || tid == 23 || tid == 24 || tid == 25 || tid == 26 || tid == 27 || tid == 28 || tid == 29){
               endY = endY - 3;
           }  
           if (tid == "R"){
               endY = endY+2;
           }       
           if (tid == "Q"){
               endY = endY-2;
               startX = startX+2
           }      
           if (tid == "P"){
               endY = endY+4;
               startX = startX+5
           }    
           if (tid == "O"){
               endY = endY+4;
               startX = startX+5
           }    
           if (tid == "N"){
               endY = endY+1;
               startX = startX+4
           }   

           if (tid == "M"){
               endY = endY+1;
               startX = startX+4
           }  

           hgt = d3.select('[rel="'+tid+'A"]').node().getBBox();
           hg1 = hgt.height/3;
           step1=true,step2=true,step3=true,step4=true,step5=true,step6=true;
           if (tid == "T"){ 
               step6 = false;
           }  
           if (tid == "R"){ 
               step6 = false;
           }  

           if (tid == "Q"){ 
               step6 = false;
           }  

           if (tid == "P"){ 
               step6 = false;
           }  

           if (tid == "O"){ 
               step6 = false;
           }  

           if (tid == "N"){ 
               step6 = false;
           }  

           if (tid == "M"){ 
               step6 = false;
           }  


           if (tid == "K"){ 
               step6 = false;
           }  


           if (tid == 20 || tid == 21 || tid == 22 || tid == 23 || tid == 24 || tid == 25 || tid == 26 || tid == 27 || tid == 28 || tid == 29){ 
               step5 = false;
               step6 = false;
           }  


           d3.select("#svg").append("g").attr("id","drawing_"+tid)      
           if (step1){
               d3.select("#drawing_"+tid).append("line").attr("id","1_"+tid).style("stroke","red")
                  .attr("x1",startX)
                  .attr("y1",endY)
                  .attr("x2",startX-4)
                  .attr("y2",endY);                  
           }

           if (step2){   
               d3.select("#drawing_"+tid).append("line").attr("id","2_"+tid).style("stroke","red")
                  .attr("x1",startX-4)
                  .attr("y1",endY)
                  .attr("x2",startX-4)
                  .attr("y2",endY+hg1);                  
           }  

           if (step3){   
               d3.select("#drawing_"+tid).append("line").attr("id","3_"+tid).style("stroke","red")
                 .attr("x1",startX-4)
                 .attr("y1",endY+hg1)
                 .attr("x2",startX-8)
                 .attr("y2",endY+hg1);                  
           }
 
           if (step4){ 
               d3.select("#drawing_"+tid).append("line").attr("id","4_"+tid).style("stroke","red")
                 .attr("x1",startX-8)
                 .attr("y1",endY+hg1)
                 .attr("x2",startX-8)
                 .attr("y2",endY+hg1+hg1);          
           }

           if (step5){  
               d3.select("#drawing_"+tid).append("line").attr("id","3_"+tid).style("stroke","red")
                 .attr("x1",startX-8)
                 .attr("y1",endY+hg1+hg1)
                 .attr("x2",startX-12)
                 .attr("y2",endY+hg1+hg1);                  
           }    

           if (step6){ 
               d3.select("#drawing_"+tid).append("line").attr("id","4_"+tid).style("stroke","red")
                 .attr("x1",startX-12)
                 .attr("y1",endY+hg1+hg1)
                 .attr("x2",startX-12)
                 .attr("y2",endY+hg1+hg1+hg1);  
           } 
       }





       if (tid == "A"  || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I" || tid == "J"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x+bbox1.width - 2; // (bbox1.width/2) ;
           endY = bbox1.y+(bbox1.height/3)+8
           if (tid == "B" || tid == "E" || tid == "F" || tid == "H"){
               endY = bbox1.y+(bbox1.height/3)+4
           }
           bbox1a = d3.select('[rel="'+tid+'A"]').node().getBBox();
           hg1 = bbox1a.height/3;
           d3.select("#svg").append("g").attr("id","drawing_"+tid)      
           step1=true,step2=true,step3=true,step4=true,step5=true,step6=true;
     

           if (tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I" || tid == "J"){
               step5 = false;
               step6 = false;
           }        


           if (step1){
               d3.select("#drawing_"+tid).append("line").attr("id","1_"+tid).style("stroke","red")
                  .attr("x1",startX)
                  .attr("y1",endY)
                  .attr("x2",startX-4)
                  .attr("y2",endY);                  
           }

           if (step2){   
               d3.select("#drawing_"+tid).append("line").attr("id","2_"+tid).style("stroke","red")
                  .attr("x1",startX-4)
                  .attr("y1",endY)
                  .attr("x2",startX-4)
                  .attr("y2",endY+hg1);                  
           }  

           if (step3){   
               d3.select("#drawing_"+tid).append("line").attr("id","3_"+tid).style("stroke","red")
                 .attr("x1",startX-4)
                 .attr("y1",endY+hg1)
                 .attr("x2",startX-8)
                 .attr("y2",endY+hg1);                  
           }
 
           if (step4){ 
               d3.select("#drawing_"+tid).append("line").attr("id","4_"+tid).style("stroke","red")
                 .attr("x1",startX-8)
                 .attr("y1",endY+hg1)
                 .attr("x2",startX-8)
                 .attr("y2",endY+hg1+hg1);          
           }

           if (step5){  
               d3.select("#drawing_"+tid).append("line").attr("id","3_"+tid).style("stroke","red")
                 .attr("x1",startX-8)
                 .attr("y1",endY+hg1+hg1)
                 .attr("x2",startX-12)
                 .attr("y2",endY+hg1+hg1);                  
           }    

           if (step6){ 
               d3.select("#drawing_"+tid).append("line").attr("id","4_"+tid).style("stroke","red")
                 .attr("x1",startX-12)
                 .attr("y1",endY+hg1+hg1)
                 .attr("x2",startX-12)
                 .attr("y2",endY+hg1+hg1+hg1);  
           } 
       }  

   }
   if (operation.toUpperCase() == "CLASS4"){
       if (parseInt(tid) > 0 && parseInt(tid) < 17){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x + 5; // (bbox1.width/2) ;
           endX = bbox1.x+bbox1.width-5;
           if (tid == 1 || tid== 2){
               endY = bbox1.y+(bbox1.height/3)+7
           }else{
               endY = bbox1.y+(bbox1.height/3)+2
               if (tid == 8){
                   endY = bbox1.y+(bbox1.height/3)
               }
               if (tid == 9 || tid == 10 || tid == 11 || tid == 12 || tid == 13){
                   endY = bbox1.y+(bbox1.height/3)-2
               }
           }
           bbox1 = d3.select('[rel="'+tid+'T"]').select('[rel="CR2"]').node().getBBox();
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           x1 = startX;
           y1 = endY;
           x2 = endX;
           y2 = endY;
           path1= this.interpolateQuadraticBezierCurve(0, 1, x1, y1, x1+((x2-x1)/2), y1-3,x2, y2);
           d3.select("#drawing_"+tid).append("path").attr("d",path1).style("fill","none").style("stroke","red");


           x1 = startX;
           y1 = endY+3;
           x2 = endX;
           y2 = endY+3;
           path2= this.interpolateQuadraticBezierCurve(0, 1, x1, y1, x1+((x2-x1)/2), y1-3,x2,y2);
           d3.select("#drawing_"+tid).append("path").attr("d",path2).style("fill","none").style("stroke","red");

           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",startX)
              .attr("y1",endY)
              .attr("x2",startX)
              .attr("y2",endY+3);    


           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",endX)
              .attr("y1",endY)
              .attr("x2",endX)
              .attr("y2",endY+3);    
       }   


       if (parseInt(tid) > 16 && parseInt(tid) < 33){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           startX = bbox1.x + 5;
           endX = (bbox1.x+bbox1.width)-5;
           hgt = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
           startY = bbox1.y+bbox1.height-hgt.height-15;
           endY = bbox1.y+bbox1.height;

           if (tid == 31 || tid == 30){
               startY = startY+2;
           }           

           if (tid == 29 || tid == 28){
               startY = startY+1;
           }           
           
           if (tid == 27){
               startY = startY + 9;   
           } 
           if (tid == 26){
              startY = startY + 2;   
           }  
 
           if (tid == 25){
              startY = startY + 7;   
           }

           if (tid == 24){
              startY = startY + 7;   
           }

           if (tid == 23){
              startY = startY + 2;   
           }

           if (tid == 22){
              startY = startY + 6;   
           }

           if (tid == 19 || tid == 18 || tid == 17){
              startY = startY + 2;   
           }

           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           x1 = startX;
           y1 = startY;
           x2 = endX;
           y2 = startY;
           path1= this.interpolateQuadraticBezierCurve(0, 1, x1, y1, x1+((x2-x1)/2), y1+3,x2, y2);
           d3.select("#drawing_"+tid).append("path").attr("d",path1).style("fill","none").style("stroke","red");
           x1 = startX;
           y1 = startY+3;
           x2 = endX;
           y2 = startY+3;
           path1= this.interpolateQuadraticBezierCurve(0, 1, x1, y1, x1+((x2-x1)/2), y1+3,x2, y2);
           d3.select("#drawing_"+tid).append("path").attr("d",path1).style("fill","none").style("stroke","red");

           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",startX)
              .attr("y1",startY)
              .attr("x2",startX)
              .attr("y2",startY+3);    


           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",endX)
              .attr("y1",startY)
              .attr("x2",endX)
              .attr("y2",startY+3);    


       }


       if (tid == "A"  || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I" || tid == "J"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x + 5; // (bbox1.width/2) ;
           endX = bbox1.x+bbox1.width-5;
           if (tid == "A"){
               endY = bbox1.y+(bbox1.height/3)+7
           }else{
               endY = bbox1.y+(bbox1.height/3)+2
               if (tid == "E" || tid == "F" || tid == 11 || tid == 12 || tid == 13){
                   endY = bbox1.y+(bbox1.height/3)-2
               }
           }
           bbox1 = d3.select('[rel="'+tid+'T"]').select('[rel="CR2"]').node().getBBox();
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           x1 = startX;
           y1 = endY;
           x2 = endX;
           y2 = endY;
           path1= this.interpolateQuadraticBezierCurve(0, 1, x1, y1, x1+((x2-x1)/2), y1-3,x2, y2);
           d3.select("#drawing_"+tid).append("path").attr("d",path1).style("fill","none").style("stroke","red");


           x1 = startX;
           y1 = endY+3;
           x2 = endX;
           y2 = endY+3;
           path2= this.interpolateQuadraticBezierCurve(0, 1, x1, y1, x1+((x2-x1)/2), y1-3,x2,y2);
           d3.select("#drawing_"+tid).append("path").attr("d",path2).style("fill","none").style("stroke","red");

           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",startX)
              .attr("y1",endY)
              .attr("x2",startX)
              .attr("y2",endY+3);    


           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",endX)
              .attr("y1",endY)
              .attr("x2",endX)
              .attr("y2",endY+3);    
       }   



       if (tid == "T" || tid == "S" || tid == "R" || tid == "Q" || tid == "P" || tid == "O" || tid == "N" || tid == "M" || tid == "L" || tid == "K"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           startX = bbox1.x + 5;
           endX = (bbox1.x+bbox1.width)-5;
           hgt = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
           startY = bbox1.y+bbox1.height-hgt.height-15;
           endY = bbox1.y+bbox1.height;

           if (tid == "Q" || tid == "S" || tid == "N"){
               startY = startY+2;
           }           

           if (tid == "T" || tid == 28){
               startY = startY+1;
           }           
           
           if (tid == "R" || tid == "P" || tid == "O"){
               startY = startY + 9;   
           } 
           if (tid == "M"){
              startY = startY + 6;   
           }  
 
           if (tid == 25){
              startY = startY + 7;   
           }

           if (tid == 24){
              startY = startY + 7;   
           }

           if (tid == 23){
              startY = startY + 2;   
           }

           if (tid == 22){
              startY = startY + 6;   
           }

           if (tid == 19 || tid == 18 || tid == 17){
              startY = startY + 2;   
           }

           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           x1 = startX;
           y1 = startY;
           x2 = endX;
           y2 = startY;
           path1= this.interpolateQuadraticBezierCurve(0, 1, x1, y1, x1+((x2-x1)/2), y1+3,x2, y2);
           d3.select("#drawing_"+tid).append("path").attr("d",path1).style("fill","none").style("stroke","red");
           x1 = startX;
           y1 = startY+3;
           x2 = endX;
           y2 = startY+3;
           path1= this.interpolateQuadraticBezierCurve(0, 1, x1, y1, x1+((x2-x1)/2), y1+3,x2, y2);
           d3.select("#drawing_"+tid).append("path").attr("d",path1).style("fill","none").style("stroke","red");

           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",startX)
              .attr("y1",startY)
              .attr("x2",startX)
              .attr("y2",startY+3);    


           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",endX)
              .attr("y1",startY)
              .attr("x2",endX)
              .attr("y2",startY+3);    
       }
   }

   if (operation.toUpperCase() == "BRIDGE"){
       if (tid > 1 && tid < 16){
           tidleft = parseFloat(tid)-1;
           tidright = parseFloat(tid)+1;
           tidcenter = tid;
           bbox1 = d3.select('[rel="'+tidleft+'T"]').node().getBBox();
           x = (bbox1.x+bbox1.width);
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           rightX1 = x;
           rightY1 = y-(bbox2.height/2)-4;

           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           x = (bbox1.x+bbox1.width);
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tidcenter+'B"]').node().getBBox();
           leftX2 = bbox1.x;



           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           x = (bbox1.x+bbox1.width);
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           rightX3 = x;
           rightY3 = y-(bbox2.height/2)-4;

           bbox1 = d3.select('[rel="'+tidright+'T"]').node().getBBox();
           x = (bbox1.x+bbox1.width);
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tidright+'B"]').node().getBBox();
           leftX4 = bbox1.x;


           d3.select("#svg").append("svg").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1);    
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1+3)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1+3);    

           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY3)
              .attr("x2",leftX4+8)
              .attr("y2",rightY3);    
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY3+3)
              .attr("x2",leftX4+8)
              .attr("y2",rightY3+3);    

           bbox1 = d3.select('[rel="'+tidleft+'A"]').node().getBoundingClientRect();
           bbox2 = d3.select('[rel="'+tidleft+'B"]').node().getBoundingClientRect();
           d3.select("#svg").append("svg").attr("id","drawing_A_"+tidleft).attr("viewBox",d3.select('[rel="'+tidleft+'A"]').attr("viewBox"))
           d3.select("#drawing_A_"+tidleft).append("path").attr("d",d3.select('[rel="'+tidleft+'A"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           d3.select("#svg").append("svg").attr("id","drawing_B_"+tidleft).attr("viewBox",d3.select('[rel="'+tidleft+'B"]').attr("viewBox"))
           d3.select("#drawing_B_"+tidleft).append("path").attr("d",d3.select('[rel="'+tidleft+'B"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           bbox1 = d3.select('[rel="'+tidcenter+'A"]').node().getBoundingClientRect();
           bbox2 = d3.select('[rel="'+tidcenter+'B"]').node().getBoundingClientRect();
           d3.select("#svg").append("svg").attr("id","drawing_A_"+tidcenter).attr("viewBox",d3.select('[rel="'+tidcenter+'A"]').attr("viewBox"))
           d3.select("#drawing_A_"+tidcenter).append("path").attr("d",d3.select('[rel="'+tidcenter+'A"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           d3.select("#svg").append("svg").attr("id","drawing_B_"+tidcenter).attr("viewBox",d3.select('[rel="'+tidcenter+'B"]').attr("viewBox"))
           d3.select("#drawing_B_"+tidcenter).append("path").attr("d",d3.select('[rel="'+tidcenter+'B"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           bbox1 = d3.select('[rel="'+tidright+'A"]').node().getBoundingClientRect();
           bbox2 = d3.select('[rel="'+tidright+'B"]').node().getBoundingClientRect();
           d3.select("#svg").append("svg").attr("id","drawing_A_"+tidright).attr("viewBox",d3.select('[rel="'+tidright+'A"]').attr("viewBox"))
           d3.select("#drawing_A_"+tidright).append("path").attr("d",d3.select('[rel="'+tidright+'A"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           d3.select("#svg").append("svg").attr("id","drawing_B_"+tidright).attr("viewBox",d3.select('[rel="'+tidright+'B"]').attr("viewBox"))
           d3.select("#drawing_B_"+tidright).append("path").attr("d",d3.select('[rel="'+tidright+'B"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")

           bbox1 = d3.select('[rel="'+tidleft+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x + bbox1.width ;
           startY = bbox1.y+(bbox1.height/3);
           rightX1 = startX;
           rightY1 = startY+8;

           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x + bbox1.width ;
           startY = bbox1.y+(bbox1.height/3);

           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x + bbox1.width ;
           startY = bbox1.y+(bbox1.height/3);
           rightX3 = startX;
           rightY3 = startY+8;

           bbox1 = d3.select('[rel="'+tidright+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x ;
           startY = bbox1.y+(bbox1.height/3);
           leftX4 = startX;



           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1);    
            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1+3)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1+3);    

            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY3)
              .attr("x2",leftX4+8)
              .attr("y2",rightY3);    
            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY3+3)
              .attr("x2",leftX4+8)
              .attr("y2",rightY3+3);  

            bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
            x1 = bbox1.x;
            y1 = bbox1.y
            x2 = bbox1.x+bbox1.width;
 
            bbox1a = d3.select('[rel="'+tidcenter+'G"]').node().getBBox();
            bbox2a = d3.select('[rel="'+tidcenter+'A"]').node().getBBox();
            y2 = bbox1a.y+(bbox1a.height - bbox2a.height);
            d3.select("#drawing_"+tid).append("line").style("stroke","red")
               .attr("x1",x1)
               .attr("y1",y1)
               .attr("x2",x2)
               .attr("y2",y2);    

            d3.select("#drawing_"+tid).append("line").style("stroke","red")
               .attr("x1",x2)
               .attr("y1",y1)
               .attr("x2",x1)
               .attr("y2",y2);    
       }

       if (tid > 17 && tid < 32){
           tidleft = parseFloat(tid)+1;
           tidright = parseFloat(tid)-1;
           tidcenter = tid;

           d3.select("#svg").append("svg").attr("id","drawing_"+tid)

           bboxa = d3.select('[rel="'+tidleft+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidleft+'B"]').node().getBBox();
           rightX1 = bboxa.x+bboxa.width;
           rightY1 = bboxa.y+(bbox2.height/2)-1;

           bboxa = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidcenter+'B"]').node().getBBox();
           leftX2 = bboxa.x;



           bboxa = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidcenter+'B"]').node().getBBox();
           rightX3 = bboxa.x+bboxa.width;
           rightY3 = bboxa.y+(bbox2.height/2)-1;

           bboxa = d3.select('[rel="'+tidright+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidright+'B"]').node().getBBox();
           leftX4 = bboxa.x;


           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1);    
            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1+3)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1+3);    

            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY1)
              .attr("x2",leftX4+8)
              .attr("y2",rightY1);    
            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY1+3)
              .attr("x2",leftX4+8)
              .attr("y2",rightY1+3);  

           bbox1 = d3.select('[rel="'+tidleft+'A"]').node().getBoundingClientRect();
           bbox2 = d3.select('[rel="'+tidleft+'B"]').node().getBoundingClientRect();
           d3.select("#svg").append("svg").attr("id","drawing_A_"+tidleft).attr("viewBox",d3.select('[rel="'+tidleft+'A"]').attr("viewBox"))
           d3.select("#drawing_A_"+tidleft).append("path").attr("d",d3.select('[rel="'+tidleft+'A"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           d3.select("#svg").append("svg").attr("id","drawing_B_"+tidleft).attr("viewBox",d3.select('[rel="'+tidleft+'B"]').attr("viewBox"))
           d3.select("#drawing_B_"+tidleft).append("path").attr("d",d3.select('[rel="'+tidleft+'B"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           bbox1 = d3.select('[rel="'+tidcenter+'A"]').node().getBoundingClientRect();
           bbox2 = d3.select('[rel="'+tidcenter+'B"]').node().getBoundingClientRect();
           d3.select("#svg").append("svg").attr("id","drawing_A_"+tidcenter).attr("viewBox",d3.select('[rel="'+tidcenter+'A"]').attr("viewBox"))
           d3.select("#drawing_A_"+tidcenter).append("path").attr("d",d3.select('[rel="'+tidcenter+'A"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           d3.select("#svg").append("svg").attr("id","drawing_B_"+tidcenter).attr("viewBox",d3.select('[rel="'+tidcenter+'B"]').attr("viewBox"))
           d3.select("#drawing_B_"+tidcenter).append("path").attr("d",d3.select('[rel="'+tidcenter+'B"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           bbox1 = d3.select('[rel="'+tidright+'A"]').node().getBoundingClientRect();
           bbox2 = d3.select('[rel="'+tidright+'B"]').node().getBoundingClientRect();
           d3.select("#svg").append("svg").attr("id","drawing_A_"+tidright).attr("viewBox",d3.select('[rel="'+tidright+'A"]').attr("viewBox"))
           d3.select("#drawing_A_"+tidright).append("path").attr("d",d3.select('[rel="'+tidright+'A"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           d3.select("#svg").append("svg").attr("id","drawing_B_"+tidright).attr("viewBox",d3.select('[rel="'+tidright+'B"]').attr("viewBox"))
           d3.select("#drawing_B_"+tidright).append("path").attr("d",d3.select('[rel="'+tidright+'B"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")


           bbox1 = d3.select('[rel="'+tidleft+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidleft+'"]').node().getBBox();
           bbox3 = d3.select('[rel="'+tidleft+'A"]').node().getBBox();
           rightX1 = bbox1.x+bbox1.width;
           rightY1 = bbox1.y+bbox1.height-bbox2.height - (bbox2.height/2)-6;

           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidcenter+'"]').node().getBBox();
           bbox3 = d3.select('[rel="'+tidcenter+'A"]').node().getBBox();
           leftX2 = bbox1.x;


           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidcenter+'"]').node().getBBox();
           bbox3 = d3.select('[rel="'+tidcenter+'A"]').node().getBBox();
           rightX3 = bbox1.x+bbox1.width;
           rightY3 = bbox1.y+bbox1.height-bbox2.height - (bbox3.height/2)-6;

           bbox1 = d3.select('[rel="'+tidright+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidright+'"]').node().getBBox();
           bbox3 = d3.select('[rel="'+tidright+'A"]').node().getBBox();
           leftX4 = bbox1.x;


           if (tidcenter == 26){
               rightY1 += 7;
           }

           if (tidcenter == 25){
               rightY1 += 4;
           }

           if (tidcenter == 24){
               rightY1 += 4;
           }

           if (tidcenter == 23){
               rightY1 += 4;
           }

           if (tidcenter == 21){
               rightY1 += 4;
           }

           if (tidcenter == 20){
               rightY1 += 3;
           }

           if (tidcenter == 19){
               rightY1 += 3;
           }

           if (tidcenter == 18){
               rightY1 += 2;
           }


           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1);    
            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1+3)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1+3);    

            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY1)
              .attr("x2",leftX4+8)
              .attr("y2",rightY1);    
            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY1+3)
              .attr("x2",leftX4+8)
              .attr("y2",rightY1+3);  

           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidcenter+'"]').node().getBBox();
           x1 = bbox1.x;
           y1 = bbox1.y+(bbox1.height - bbox2.height);
           x2 = bbox1.x+bbox1.width;
           y2 = bbox1.y+bbox1.height;

           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",x1)
              .attr("y1",y1)
              .attr("x2",x2)
              .attr("y2",y2);    

           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",x2)
              .attr("y1",y1)
              .attr("x2",x1)
              .attr("y2",y2);    
       }
       if (tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I"){
           if (tid == "B"){
               tidcenter = "B";
               tidleft = "A";
               tidright = "C"
           }
           if (tid == "C"){
               tidcenter = "C";
               tidleft = "B";
               tidright = "D"
           }
           if (tid == "D"){
               tidcenter = "D";
               tidleft = "C";
               tidright = "E"
           }
           if (tid == "E"){
               tidcenter = "E";
               tidleft = "D";
               tidright = "F"
           }
           if (tid == "F"){
               tidcenter = "F";
               tidleft = "E";
               tidright = "G"
           }
           if (tid == "G"){
               tidcenter = "G";
               tidleft = "F";
               tidright = "H"
           }
           if (tid == "H"){
               tidcenter = "H";
               tidleft = "G";
               tidright = "I"
           }
           if (tid == "I"){
               tidcenter = "I";
               tidleft = "H";
               tidright = "J"
           }
           bbox1 = d3.select('[rel="'+tidleft+'T"]').node().getBBox();
           x = (bbox1.x+bbox1.width);
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           rightX1 = x;
           rightY1 = y-(bbox2.height/2)-4;

           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           x = (bbox1.x+bbox1.width);
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tidcenter+'B"]').node().getBBox();
           leftX2 = bbox1.x;



           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           x = (bbox1.x+bbox1.width);
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           rightX3 = x;
           rightY3 = y-(bbox2.height/2)-4;


           bbox1 = d3.select('[rel="'+tidright+'T"]').node().getBBox();
           x = (bbox1.x+bbox1.width);
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tidright+'B"]').node().getBBox();
           leftX4 = bbox1.x;


           d3.select("#svg").append("svg").attr("id","drawing_"+tid)

           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1);    
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1+3)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1+3);    

           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY3)
              .attr("x2",leftX4+8)
              .attr("y2",rightY3);    
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY3+3)
              .attr("x2",leftX4+8)
              .attr("y2",rightY3+3);    

           bbox1 = d3.select('[rel="'+tidleft+'A"]').node().getBoundingClientRect();
           bbox2 = d3.select('[rel="'+tidleft+'B"]').node().getBoundingClientRect();
           d3.select("#svg").append("svg").attr("id","drawing_A_"+tidleft).attr("viewBox",d3.select('[rel="'+tidleft+'A"]').attr("viewBox"))
           d3.select("#drawing_A_"+tidleft).append("path").attr("d",d3.select('[rel="'+tidleft+'A"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           d3.select("#svg").append("svg").attr("id","drawing_B_"+tidleft).attr("viewBox",d3.select('[rel="'+tidleft+'B"]').attr("viewBox"))
           d3.select("#drawing_B_"+tidleft).append("path").attr("d",d3.select('[rel="'+tidleft+'B"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           bbox1 = d3.select('[rel="'+tidcenter+'A"]').node().getBoundingClientRect();
           bbox2 = d3.select('[rel="'+tidcenter+'B"]').node().getBoundingClientRect();
           d3.select("#svg").append("svg").attr("id","drawing_A_"+tidcenter).attr("viewBox",d3.select('[rel="'+tidcenter+'A"]').attr("viewBox"))
           d3.select("#drawing_A_"+tidcenter).append("path").attr("d",d3.select('[rel="'+tidcenter+'A"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           d3.select("#svg").append("svg").attr("id","drawing_B_"+tidcenter).attr("viewBox",d3.select('[rel="'+tidcenter+'B"]').attr("viewBox"))
           d3.select("#drawing_B_"+tidcenter).append("path").attr("d",d3.select('[rel="'+tidcenter+'B"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           bbox1 = d3.select('[rel="'+tidright+'A"]').node().getBoundingClientRect();
           bbox2 = d3.select('[rel="'+tidright+'B"]').node().getBoundingClientRect();
           d3.select("#svg").append("svg").attr("id","drawing_A_"+tidright).attr("viewBox",d3.select('[rel="'+tidright+'A"]').attr("viewBox"))
           d3.select("#drawing_A_"+tidright).append("path").attr("d",d3.select('[rel="'+tidright+'A"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           d3.select("#svg").append("svg").attr("id","drawing_B_"+tidright).attr("viewBox",d3.select('[rel="'+tidright+'B"]').attr("viewBox"))
           d3.select("#drawing_B_"+tidright).append("path").attr("d",d3.select('[rel="'+tidright+'B"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")

           bbox1 = d3.select('[rel="'+tidleft+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x + bbox1.width ;
           startY = bbox1.y+(bbox1.height/3);
           rightX1 = startX;
           rightY1 = startY+8;

           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x + bbox1.width ;
           startY = bbox1.y+(bbox1.height/3);

           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x + bbox1.width ;
           startY = bbox1.y+(bbox1.height/3);
           rightX3 = startX;
           rightY3 = startY+8;

           bbox1 = d3.select('[rel="'+tidright+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x ;
           startY = bbox1.y+(bbox1.height/3);
           leftX4 = startX;


           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1);    
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1+3)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1+3);    
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY3)
              .attr("x2",leftX4+8)
              .attr("y2",rightY3);    
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY3+3)
              .attr("x2",leftX4+8)
              .attr("y2",rightY3+3);  

           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           x1 = bbox1.x;
           y1 = bbox1.y
           x2 = bbox1.x+bbox1.width;
 
           bbox1a = d3.select('[rel="'+tidcenter+'G"]').node().getBBox();
           bbox2a = d3.select('[rel="'+tidcenter+'A"]').node().getBBox();
           y2 = bbox1a.y+(bbox1a.height - bbox2a.height);
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",x1)
              .attr("y1",y1)
              .attr("x2",x2)
              .attr("y2",y2);    

           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",x2)
              .attr("y1",y1)
              .attr("x2",x1)
              .attr("y2",y2);    
       }

       if (tid == "S" || tid == "R" || tid == "Q" || tid == "P" || tid == "O" || tid == "N" || tid == "M" || tid == "L"){
           if (tid == "S"){    
               tidleft = "T"
               tidcenter = "S"
               tidright = "R"
           } 
           if (tid == "R"){    
               tidleft = "S"
               tidcenter = "R"
               tidright = "Q"
           } 
           if (tid == "Q"){    
               tidleft = "R"
               tidcenter = "Q"
               tidright = "P"
           } 
           if (tid == "P"){    
               tidleft = "Q"
               tidcenter = "P"
               tidright = "O"
           } 
           if (tid == "O"){    
               tidleft = "P"
               tidcenter = "O"
               tidright = "N"
           } 
           if (tid == "N"){    
               tidleft = "O"
               tidcenter = "N"
               tidright = "M"
           } 
           if (tid == "M"){    
               tidleft = "N"
               tidcenter = "M"
               tidright = "L"
           } 
           if (tid == "L"){    
               tidleft = "M"
               tidcenter = "L"
               tidright = "K"
           } 

           d3.select("#svg").append("svg").attr("id","drawing_"+tid)

           bboxa = d3.select('[rel="'+tidleft+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidleft+'B"]').node().getBBox();
           rightX1 = bboxa.x+bboxa.width;
           rightY1 = bboxa.y+(bbox2.height/2)-1;

           bboxa = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidcenter+'B"]').node().getBBox();
           leftX2 = bboxa.x;



           bboxa = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidcenter+'B"]').node().getBBox();
           rightX3 = bboxa.x+bboxa.width;
           rightY3 = bboxa.y+(bbox2.height/2)-1;

           bboxa = d3.select('[rel="'+tidright+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidright+'B"]').node().getBBox();
           leftX4 = bboxa.x;


           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1);    
            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1+3)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1+3);    

            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY1)
              .attr("x2",leftX4+8)
              .attr("y2",rightY1);    
            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY1+3)
              .attr("x2",leftX4+8)
              .attr("y2",rightY1+3);  

           bbox1 = d3.select('[rel="'+tidleft+'A"]').node().getBoundingClientRect();
           bbox2 = d3.select('[rel="'+tidleft+'B"]').node().getBoundingClientRect();
           d3.select("#svg").append("svg").attr("id","drawing_A_"+tidleft).attr("viewBox",d3.select('[rel="'+tidleft+'A"]').attr("viewBox"))
           d3.select("#drawing_A_"+tidleft).append("path").attr("d",d3.select('[rel="'+tidleft+'A"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           d3.select("#svg").append("svg").attr("id","drawing_B_"+tidleft).attr("viewBox",d3.select('[rel="'+tidleft+'B"]').attr("viewBox"))
           d3.select("#drawing_B_"+tidleft).append("path").attr("d",d3.select('[rel="'+tidleft+'B"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           bbox1 = d3.select('[rel="'+tidcenter+'A"]').node().getBoundingClientRect();
           bbox2 = d3.select('[rel="'+tidcenter+'B"]').node().getBoundingClientRect();
           d3.select("#svg").append("svg").attr("id","drawing_A_"+tidcenter).attr("viewBox",d3.select('[rel="'+tidcenter+'A"]').attr("viewBox"))
           d3.select("#drawing_A_"+tidcenter).append("path").attr("d",d3.select('[rel="'+tidcenter+'A"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           d3.select("#svg").append("svg").attr("id","drawing_B_"+tidcenter).attr("viewBox",d3.select('[rel="'+tidcenter+'B"]').attr("viewBox"))
           d3.select("#drawing_B_"+tidcenter).append("path").attr("d",d3.select('[rel="'+tidcenter+'B"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           bbox1 = d3.select('[rel="'+tidright+'A"]').node().getBoundingClientRect();
           bbox2 = d3.select('[rel="'+tidright+'B"]').node().getBoundingClientRect();
           d3.select("#svg").append("svg").attr("id","drawing_A_"+tidright).attr("viewBox",d3.select('[rel="'+tidright+'A"]').attr("viewBox"))
           d3.select("#drawing_A_"+tidright).append("path").attr("d",d3.select('[rel="'+tidright+'A"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
           d3.select("#svg").append("svg").attr("id","drawing_B_"+tidright).attr("viewBox",d3.select('[rel="'+tidright+'B"]').attr("viewBox"))
           d3.select("#drawing_B_"+tidright).append("path").attr("d",d3.select('[rel="'+tidright+'B"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")


           bbox1 = d3.select('[rel="'+tidleft+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidleft+'"]').node().getBBox();
           bbox3 = d3.select('[rel="'+tidleft+'A"]').node().getBBox();
           rightX1 = bbox1.x+bbox1.width;
           rightY1 = bbox1.y+bbox1.height-bbox2.height - (bbox2.height/2)-6;

           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidcenter+'"]').node().getBBox();
           bbox3 = d3.select('[rel="'+tidcenter+'A"]').node().getBBox();
           leftX2 = bbox1.x;


           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidcenter+'"]').node().getBBox();
           bbox3 = d3.select('[rel="'+tidcenter+'A"]').node().getBBox();
           rightX3 = bbox1.x+bbox1.width;
           rightY3 = bbox1.y+bbox1.height-bbox2.height - (bbox3.height/2)-6;

           bbox1 = d3.select('[rel="'+tidright+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidright+'"]').node().getBBox();
           bbox3 = d3.select('[rel="'+tidright+'A"]').node().getBBox();
           leftX4 = bbox1.x;


           if (tidcenter == "Q"){
               rightY1 += 11;
           }

           if (tidcenter == "P"){
               rightY1 += 4;
           }

           if (tidcenter == "O"){
               rightY1 += 10;
           }

           if (tidcenter == "N"){
               rightY1 += 10;
           }

           if (tidcenter == "M"){
               rightY1 += 4;
           }

           if (tidcenter == "L"){
               rightY1 += 5;
           }



           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1);    
            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX1-8)
              .attr("y1",rightY1+3)
              .attr("x2",leftX2+8)
              .attr("y2",rightY1+3);    

            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY1)
              .attr("x2",leftX4+8)
              .attr("y2",rightY1);    
            d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",rightX3-8)
              .attr("y1",rightY1+3)
              .attr("x2",leftX4+8)
              .attr("y2",rightY1+3);  

           bbox1 = d3.select('[rel="'+tidcenter+'T"]').node().getBBox();
           bbox2 = d3.select('[rel="'+tidcenter+'"]').node().getBBox();
           x1 = bbox1.x;
           y1 = bbox1.y+(bbox1.height - bbox2.height);
           x2 = bbox1.x+bbox1.width;
           y2 = bbox1.y+bbox1.height;

           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",x1)
              .attr("y1",y1)
              .attr("x2",x2)
              .attr("y2",y2);    

           d3.select("#drawing_"+tid).append("line").style("stroke","red")
              .attr("x1",x2)
              .attr("y1",y1)
              .attr("x2",x1)
              .attr("y2",y2);    

       }


   }

   if (operation.toUpperCase() == "ROOTCANAL1"){
       if (rootcanal1.indexOf(";"+tid+";") > -1){
           if (parseInt(tid) > 0 && parseInt(tid) < 17){
               bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
               startX = bbox1.x + (bbox1.width/2) ;
               endX = (bbox1.x+(bbox1.width/2));
               startY = bbox1.y+(bbox1.height/3);
               endY = bbox1.y;
               path= this.interpolateQuadraticBezierCurve(0, 1, startX+1, startY+1, startX-2, startY,endX+1, endY-1);
               if (tid == 4){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-2, startX-2, startY,endX+1, endY);
               }
               if (tid == 5){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+1, startY-2, startX-2, startY,endX, endY);
               }
               if (tid == 6){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY+1, startX-2, startY,endX+1.5, endY);
               }
               if (tid == 7){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+2, startY-1, startX-1, startY,endX+3.5, endY);
               }
               if (tid == 8){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+1, startY-5, startX-1, startY,endX, endY);
               }
               if (tid == 9){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-5, startX-2, startY,endX-1, endY);
               }
               if (tid == 10){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+1, startY-5, startX, startY,endX+3, endY);
               }
               if (tid == 11){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-4.5, startX-3, startY-3,endX+2, endY);
               }
               if (tid == 12){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+1, startY-4.5, startX-1, startY-3,endX, endY);
               }
               if (tid == 13){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-4.5, startX-1, startY-3,endX+1, endY);
               }


               d3.select("#svg").append("g").attr("id","drawing_"+tid)
               d3.select("#drawing_"+tid).append("path").attr("d",path).style("fill","none").style("stroke","red");
           }   
           if (parseInt(tid) > 16 && parseInt(tid) < 33){
               bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
               startX = bbox1.x + (bbox1.width/2) ;
               endX = (bbox1.x+(bbox1.width/2));
               hgt = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
               startY = bbox1.y+bbox1.height-hgt.height;
               endY = bbox1.y+bbox1.height;
               if (tid == 32 || tid == 17){  
                   if (tid == 32){  
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX+3, startY-10,startX-3, startY,endX+8, endY-1);
                   }else{
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX+1, startY-7, startX-3, startY,endX+6, endY-2);
                   }
               }else{
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-8, startX-3, startY,endX+1, endY);
                   if (tid == 25){
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-3, startX-1, startY,endX+1, endY);
                   }        
                   if (tid == 27){
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-2, startX-3, startY,endX, endY);
                   }        
                   if (tid == 24){
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX+4, startY-2, startX+2, startY,endX+3, endY-1);
                   }        
                   if (tid == 23){
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX+1, startY-7, startX-2, startY,endX, endY);
                   }        
                   if (tid == 22){
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-3, startX-2, startY,endX-1, endY);
                   }        
                   if (tid == 26){
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX+1, startY-7, startX-2, startY,endX, endY);
                   }        
                   if (tid == 21){
                       path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-8, startX-1, startY,endX, endY);
                   }        
               }
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
               d3.select("#drawing_"+tid).append("path").attr("d",path).style("fill","none").style("stroke","red");
           } 
           if (tid == "A" || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I" || tid == "J"){
               bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
//               bbox1a = bbox1;
//               startX = bbox1.x + (bbox1.width/2) ;
//               endX = (bbox1.x+(bbox1.width/3))+2;
//               startY = bbox1.y+(bbox1.height/3);
//               endY = bbox1.y+5;
               startX = bbox1.x + (bbox1.width/2) ;
               endX = (bbox1.x+(bbox1.width/2));
               startY = bbox1.y+(bbox1.height/3);
               endY = bbox1.y;
               path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY+2, endX+(bbox1.width/3), endY,endX, endY);
               if (tid == "C"){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX-1, startY+1, startX-3, startY-5,endX, endY);
               }
               if (tid == "D"){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+2, startY+1, startX, startY-5,endX+4, endY);
               }
               if (tid == "E"){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX-1, startY-7, startX, startY-5,endX-2, endY);
               }
               if (tid == "F"){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX-1, startY-7, startX, startY-5,endX-2, endY);
               }
               if (tid == "G"){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX+2, startY-2, startX, startY-5,endX+4, endY);
               }
               if (tid == "H"){
                   path= this.interpolateQuadraticBezierCurve(0, 1, startX-1, startY-2, startX-3, startY-5,endX+1, endY);
               }

               d3.select("#svg").append("g").attr("id","drawing_"+tid)
               d3.select("#drawing_"+tid).append("path").attr("d",path).style("fill","none").style("stroke","red");
            }
            if (tid == "K" || tid == "L" || tid == "M" || tid == "N" || tid == "O" || tid == "P" || tid == "Q" || tid == "R" || tid == "S" || tid == "T"){
                bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
                startX = bbox1.x + (bbox1.width/2) ;
                endX = (bbox1.x+(bbox1.width/2));
                hgt = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
                startY = bbox1.y+bbox1.height-hgt.height;
                endY = bbox1.y+bbox1.height;
                path= this.interpolateQuadraticBezierCurve(0, 1, startX-2, startY-7, endX-1, endY,endX-2, endY-1);
                if (tid == "R"){
                    path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY, endX+2, endY,endX-2, endY);
                }
                if (tid == "Q"){
                    path= this.interpolateQuadraticBezierCurve(0, 1, startX-2, startY-7, endX-1, endY,endX-2, endY-1);
                }
                if (tid == "P"){
                    path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-3, endX-1, endY,endX, endY-1);
                }
                if (tid == "O"){
                    path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-2, endX-1, endY,endX+2, endY-1);
                }
                if (tid == "N"){
                    path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-8, endX-1, endY,endX+1, endY-1);
                }
                if (tid == "M"){
                    path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY-3, endX-1, endY,endX, endY-1);
                }
                d3.select("#svg").append("g").attr("id","drawing_"+tid)
                d3.select("#drawing_"+tid).append("path").attr("d",path).style("fill","none").style("stroke","red");
            }
       }  
   }
   if (operation.toUpperCase() == "ROOTCANAL2"){
       if (rootcanal2.indexOf(";"+tid+";") > -1){
           if (parseInt(tid) > 0 && parseInt(tid) < 17){
               bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
               startX = bbox1.x + (bbox1.width/2) ;
               endX = (bbox1.x+(bbox1.width/2));
               startY = bbox1.y+(bbox1.height/3);
               endY = bbox1.y;
               path1= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX-8, startY,endX+1, endY-1);
               path2= this.interpolateQuadraticBezierCurve(0, 1, startX+5, startY+1, startX+8, startY,startX+4, endY-1);
               path3= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX, startY-3,startX+5, startY+1);
               if (tid === 1){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX-8, startY,endX+1, endY+1);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+5, startY+1, startX+8, startY,startX+5, endY+1);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX, startY-3,startX+5, startY+1);
               } 
               if (tid === 16){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX-8, startY,endX+1, endY+1);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+5, startY+1, startX+8, startY,startX+5, endY+1);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX, startY-3,startX+5, startY+1);
               } 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
               d3.select("#drawing_"+tid).append("path").attr("d",path1).style("fill","none").style("stroke","red");
               d3.select("#drawing_"+tid).append("path").attr("d",path2).style("fill","none").style("stroke","red");
               d3.select("#drawing_"+tid).append("path").attr("d",path3).style("fill","none").style("stroke","red");
           }   
           if (parseInt(tid) == 31 || parseInt(tid) == 30 || parseInt(tid) == 18 || parseInt(tid) == 19 || tid == "T" || tid == "S" || tid == "L" || tid == "K" ){
               bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
               startX = bbox1.x + (bbox1.width/2) ;
               endX = (bbox1.x+(bbox1.width/2));
               hgt = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
               startY = bbox1.y+bbox1.height-hgt.height;
               endY = bbox1.y+bbox1.height;
               path1= this.interpolateQuadraticBezierCurve(0, 1, startX-2, startY+1, startX-8, startY,endX+1, endY-1);
               path2= this.interpolateQuadraticBezierCurve(0, 1, startX+5, startY+1, startX+8, startY,startX+4, endY-1);
               path3= this.interpolateQuadraticBezierCurve(0, 1, startX-6, startY-4, startX, startY-5,startX+9, startY-5);
               if (tid == 31){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-6, startY-5, startX-9, startY+5,endX+2, endY);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+9, startY-5, startX+11, startY+5,startX+9, endY-2);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-6, startY-4, startX, startY-5,startX+9, startY-5);
               } 
               if (tid == "T"){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-6, startY-5, startX-9, startY+5,endX+2, endY);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+9, startY-5, startX+11, startY+5,startX+9, endY-2);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-6, startY-4, startX, startY-5,startX+9, startY-5);
               } 
               if (tid == "L"){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-8, startY-5, startX-12, startY+5,endX-9, endY);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+5, startY-5, startX+7, startY+5,startX+4, endY);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-8, startY-5, startX, startY-5,startX+5, startY-5);
               } 

               if (tid == 30){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-6, startY-5, startX-9, startY+5,endX-6, endY);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+7, startY-5, startX+9, startY+5,startX+7, endY);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-6, startY-5, startX, startY-5,startX+7, startY-5);
               } 
               if (tid == "S"){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-7, startY-5, startX-11, startY+5,endX-9, endY);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+4, startY-5, startX+7, startY+5,startX+4, endY);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-7, startY-5, startX, startY-5,startX+4, startY-5);
               } 
               if (tid == "K"){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-2, startY-3, startX-8, startY+5,endX+3, endY);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+7, startY-5, startX+11, startY+5,startX+10, endY-3);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-2, startY-3, startX+1, startY-2,startX+7, startY-5);
               } 


               if (tid == 18){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-6, startY-5, startX-9, startY+5,endX+1, endY+1);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+7, startY-5, startX+9, startY+5,startX+7, endY-2);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-6, startY-4, startX, startY-5,startX+7, startY-5);
               } 
               if (tid == 19){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-6, startY-5, startX-9, startY+5,endX-6, endY);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+7, startY-5, startX+9, startY+5,startX+7, endY);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-6, startY-4, startX, startY-5,startX+7, startY-5);
               } 

               d3.select("#svg").append("g").attr("id","drawing_"+tid)
               d3.select("#drawing_"+tid).append("path").attr("d",path1).style("fill","none").style("stroke","red");
               d3.select("#drawing_"+tid).append("path").attr("d",path2).style("fill","none").style("stroke","red");
               d3.select("#drawing_"+tid).append("path").attr("d",path3).style("fill","none").style("stroke","red");
           }   

       }  
   }
   if (operation.toUpperCase() == "ROOTCANAL3"){
       if (rootcanal3.indexOf(tid+";") > -1){
           if (tid == "3" ||  tid == "14" || tid == "B" || tid == "I"){   

               bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
               startX = bbox1.x + (bbox1.width/2) ;
               endX = (bbox1.x+(bbox1.width/2));
               startY = bbox1.y+(bbox1.height/3);
               endY = bbox1.y;
               path1= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX-8, startY,endX+1, endY-1);
               path2= this.interpolateQuadraticBezierCurve(0, 1, startX+5, startY+1, startX+8, startY,startX+4, endY-1);
               path3= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX, startY-3,startX+5, startY+1);
               if (tid == 3){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY-3, startX-9, startY-13,endX-6, endY);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+7, startY-3, startX+10, startY-13,startX+9, endY+3);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY-3, startX, startY-7,startX+7, startY-5);
                   path4= this.interpolateQuadraticBezierCurve(0, 1, startX+2, startY-3, startX, startY,endX+2, endY);
               } 
               if (tid == 14){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY-3, startX-9, startY-13,endX-6, endY);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+7, startY-3, startX+10, startY-13,startX+9, endY+3);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY-3, startX, startY-7,startX+7, startY-5);
                   path4= this.interpolateQuadraticBezierCurve(0, 1, startX+2, startY-3, startX, startY,endX+2, endY);
               } 

               if (tid == "B"){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-8, startY-3, startX-12, startY-13,endX-9, endY+1);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+5, startY-3, startX+10, startY-13,startX+5, endY+3);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-8, startY-3, startX, startY-7,startX+5, startY-3);
                   path4= this.interpolateQuadraticBezierCurve(0, 1, startX-2, startY-3, startX, startY,endX-2, endY);
               } 
               if (tid == "I"){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-8, startY-3, startX-12, startY-13,endX-9, endY+1);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+5, startY-3, startX+10, startY-13,startX+5, endY+3);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-8, startY-3, startX, startY-7,startX+5, startY-3);
                   path4= this.interpolateQuadraticBezierCurve(0, 1, startX-2, startY-3, startX, startY,endX-2, endY);
               } 


               d3.select("#svg").append("g").attr("id","drawing_"+tid)
               d3.select("#drawing_"+tid).append("path").attr("d",path1).style("fill","none").style("stroke","red");
               d3.select("#drawing_"+tid).append("path").attr("d",path2).style("fill","none").style("stroke","red");
               d3.select("#drawing_"+tid).append("path").attr("d",path3).style("fill","none").style("stroke","red");
               d3.select("#drawing_"+tid).append("path").attr("d",path4).style("fill","none").style("stroke","red");
           }

           if (tid == "2" ||  tid == "15" || tid == "A" || tid == "J"){   

               bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
               startX = bbox1.x + (bbox1.width/2) ;
               endX = (bbox1.x+(bbox1.width/2));
               startY = bbox1.y+(bbox1.height/3);
               endY = bbox1.y;
               path1= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX-8, startY,endX+1, endY-1);
               path2= this.interpolateQuadraticBezierCurve(0, 1, startX+5, startY+1, startX+8, startY,startX+4, endY-1);
               path3= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX, startY-3,startX+5, startY+1);
               if (tid == 2){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX-7, startY-13,endX+1, endY+2);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+6, startY+1, startX+9, startY-13,startX+5, endY+6);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX, startY-3,startX+5, startY+1);
                   path4= this.interpolateQuadraticBezierCurve(0, 1, startX+4, startY, startX, startY,endX+4, endY+1);
               } 
               if (tid == 15){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX-7, startY-13,endX+1, endY+3);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+6, startY-1, startX+9, startY-13,startX+2, endY+5);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+1, startX, startY-3,startX+6, startY-1);
                   path4= this.interpolateQuadraticBezierCurve(0, 1, startX+2, startY, startX, startY,endX+2, endY+1);
               } 

               if (tid == "A"){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+3, startX-5, startY-16,endX+1, endY+2);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+7, startY+2, startX+7, startY-16,startX+4, endY+7);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-5, startY+3, startX, startY-3,startX+7, startY+2);
                   path4= this.interpolateQuadraticBezierCurve(0, 1, startX+3, startY, startX, startY,endX+2, endY+1);
               } 
               if (tid == "J"){
                   path1= this.interpolateQuadraticBezierCurve(0, 1, startX-6, startY+1, startX-9, startY-13,endX+1, endY+3);
                   path2= this.interpolateQuadraticBezierCurve(0, 1, startX+6, startY-1, startX+7, startY-13,startX+2, endY+4);
                   path3= this.interpolateQuadraticBezierCurve(0, 1, startX-6, startY+1, startX, startY-3,startX+6, startY-1);
                   path4= this.interpolateQuadraticBezierCurve(0, 1, startX-1, startY, startX, startY,endX, endY+1);
               } 


               d3.select("#svg").append("g").attr("id","drawing_"+tid)
               d3.select("#drawing_"+tid).append("path").attr("d",path1).style("fill","none").style("stroke","red");
               d3.select("#drawing_"+tid).append("path").attr("d",path2).style("fill","none").style("stroke","red");
               d3.select("#drawing_"+tid).append("path").attr("d",path3).style("fill","none").style("stroke","red");
               d3.select("#drawing_"+tid).append("path").attr("d",path4).style("fill","none").style("stroke","red");



//               bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
//               startX = bbox1.x + (bbox1.width/2) ;
//               endX = (bbox1.x+(bbox1.width/2));
//               startY = bbox1.y+(bbox1.height/3);
//               endY = bbox1.y;
//               d3.select("#svg").append("g").attr("id","drawing_"+tid)
//               if (tid == "J"){
//                   startX = startX-2;
//                   endX = endX - 2;
//                   endY = endY + 3;
//               } 
//               if (tid == "A"){
//                   startX = startX-2;
//                   endX = endX - 2;
//                   endY = endY + 3;
//               } 
//               path= interpolateQuadraticBezierCurve(0, 1, startX-4, startY, startX-4, endY+5,endX+2, endY+5);
//               d3.select("#drawing_"+tid).append("path").attr("d",path).style("fill","none").style("stroke","red");
           }
//               path= interpolateQuadraticBezierCurve(0, 1, startX+2, startY+1, startX-2, startY,startX+2, endY-1);
//               d3.select("#drawing_"+tid).append("path").attr("d",path).style("fill","none").style("stroke","red");
       }  
   }
   if (operation.toUpperCase() == "CLASS3"){
       if (parseInt(tid) > 0 && parseInt(tid) < 17){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x + 5; // (bbox1.width/2) ;
           endX = (bbox1.x+(bbox1.width/3))+2;
           startY = bbox1.y+(bbox1.height/3);
           endY = bbox1.y+5;
           bbox1 = d3.select('[rel="'+tid+'T"]').select('[rel="CR2"]').node().getBBox();
           x = startX;
           y = startY;
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("ellipse").attr("id","el"+tid).style("stroke","red").style("fill","none")
             .attr("cx",startX-1)
             .attr("cy",startY+10)
             .attr("ry",(6/2))
             .attr("rx",1.5)

           centre = d3.select("#el"+tid).node().getBBox();      
           rotate = 10
           d3.select("#el"+tid).attr("transform", "rotate(" + rotate + ", " +  (centre.x + centre.width / 2) + ", " + (centre.y + centre.height / 2) + ")");
       }   

       if (parseInt(tid) > 16 && parseInt(tid) < 33){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           startX = bbox1.x + bbox1.width - 3 ;
           hgt = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
           startY = bbox1.y+bbox1.height-hgt.height-10;
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           if (tid == 27){
               startY += 9;
           }    
           if (tid == 24){
               startY += 2;
           } 
           if (tid == 25){
               startY += 2;
           } 
           if (tid == 22){
               startY += 2;
           } 

           d3.select("#drawing_"+tid).append("ellipse").attr("id","el"+tid).style("stroke","red").style("fill","none")
             .attr("cx",startX-1)
             .attr("cy",startY-10)
             .attr("ry",(6/2))
             .attr("rx",1.5)

           centre = d3.select("#el"+tid).node().getBBox();      
           rotate = 10
           d3.select("#el"+tid).attr("transform", "rotate(" + rotate + ", " +  (centre.x + centre.width / 2) + ", " + (centre.y + centre.height / 2) + ")");
       }   
   } 

   if (operation.toUpperCase().indexOf(";;CERVICAL-BUCCAL;;") > -1){
       if (parseFloat(tid) < 17){
           bbox1 = d3.select('[rel="'+tid+'G"]').node().getBBox();
           bbox1a = bbox1-1;
           startX = bbox1.x+3; 
           endX = bbox1.x+bbox1.width-2;
           startY = bbox1.y;
           if (tid == 1){
               startY = startY-5;
           } 
           if (tid == 2){
               startY = startY-4;
           } 
           if (tid == 3){
               startY = startY-4;
           } 
           if (tid == 4){
               startY = startY-4;
           } 
           if (tid == 5){
               startY = startY-4;
           } 
           if (tid == 7){
               startY = startY-16;
               startX += 2;
               endX -= 2;  
           } 
           if (tid == 8){
               startY = startY-1;
               startX += 1;
               endX -= 2;  
           } 
           if (tid == 9){
               startY = startY-1;
               startX += 1;
               endX -= 2;  
           }
           if (tid == 10){
               startY = startY-5;
               startX += 2;
               endX -= 2;  
           }
           if (tid == 11){
               startY = startY-2;
               startX += 2;
               endX -= 2;  
           }
           if (tid == 12){
               startY = startY-5;
               startX += 2;
               endX -= 2;  
           }
           if (tid == 13){
               startY = startY-5;
               startX += 2;
               endX -= 2;  
           }
           if (tid == 14){
               startY = startY-5;
               startX += 2;
               endX -= 2;  
           }
           if (tid == 15){
               startY = startY-5;
               startX += 2;
               endX -= 2;  
           }
           if (tid == 16){
               startY = startY-5;
               startX += 2;
               endX -= 2;  
           }
           endY = startY+bbox1.height; 
           bbox1 = d3.select('[rel="'+tid+'A"]').node().getBBox();
           startY = endY-bbox1.height;
           endY = startY+10;
           points = [{
               x: startX, y: startY
           },{
              x: endX, y: startY
           },{
              x: endX+3, y: startY+8
           },{
              x: startX-3, y: startY+8
            }];
            d3.select("#svg").append("g").attr("id","drawing_"+tid)
            line = d3.line()
                .x(function(d) {
                    return d.x;
                })
                .y(function(d) {
                   return d.y;
                });
            d3.select("#drawing_"+tid).append("path").attr("d", line(points) + 'Z').style("fill", "red")
       }
       if (tid == "A" || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I" || tid == "J"){
           bbox1 = d3.select('[rel="'+tid+'G"]').node().getBBox();
           bbox1a = bbox1-1;
           startX = bbox1.x+3; 
           endX = bbox1.x+bbox1.width-2;
           startY = bbox1.y;
           if (tid == "A"){
               startY = startY-5;
               startX += 1;
               endX -= 1;  
           } 
           if (tid == "B"){
               startY = startY-4;
               startX += 1;
               endX -= 1;  
           } 
           if (tid == "C"){
               startY = startY-2;
               startX += 2;
               endX -= 2;  
           } 
           if (tid == "D"){
               startY = startY-5;
               startX += 3;
               endX -= 1;  
           } 
           if (tid == "E"){
               startY = startY-4;
               startX += 2;
               endX -= 2;  
           } 
           if (tid == "F"){
               startY = startY-4;
               startX += 2;
               endX -= 2;  
           } 
           if (tid == "G"){
               startY = startY-4;
               startX += 1;
           } 
           if (tid == "H"){
               startY = startY-1;
               startX += 1;
               endX -= 2;  
           }
           if (tid == "I"){
               startY = startY-5;
               startX += 2;
               endX -= 2;  
           }
           if (tid == "J"){
               startY = startY-2;
               startX += 2;
               endX -= 2;  
           }
           endY = startY+bbox1.height; 
           bbox1 = d3.select('[rel="'+tid+'A"]').node().getBBox();
           startY = endY-bbox1.height;
           endY = startY+10;
           points = [{
               x: startX, y: startY
           },{
              x: endX, y: startY
           },{
              x: endX+3, y: startY+8
           },{
              x: startX-3, y: startY+8
            }];
            d3.select("#svg").append("g").attr("id","drawing_"+tid)
            line = d3.line()
                .x(function(d) {
                    return d.x;
                })
                .y(function(d) {
                   return d.y;
                });
            d3.select("#drawing_"+tid).append("path").attr("d", line(points) + 'Z').style("fill", "red")
       } 
   }

   if (operation.toUpperCase().indexOf(";;CERVICAL-LINGUAL;;") > -1){
       if (parseFloat(tid) > 16 && parseFloat(tid) < 33){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           bbox1a = bbox1-1;
           startX = bbox1.x+3; 
           endX = bbox1.x+bbox1.width-2;
           startY = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
           startY = startY - bbox2.height;
           bbox3 = d3.select('[rel="'+tid+'A"]').node().getBBox();
           startY = startY - bbox3.height;
           if (tid == 32){
               startY = startY-14;
           } 
           if (tid == 31){
               startY = startY-9;
           } 
           if (tid == 30){
               startY = startY-9;
           } 
           if (tid == 29){
               startY = startY-9;
           } 
           if (tid == 28){
               startY = startY-9;
           } 
           if (tid == 27){
               startY = startY+3;
               endX = endX - 2;
           } 
           if (tid == 26){
               startY = startY-5;
               startX -= 1;
           } 
           if (tid == 25){
               startY = startY-2;
               startX -= 1;
           }
           if (tid == 24){
               startY = startY-3;
               startX += 2;
           }
           if (tid == 23){
               startY = startY-5;
               startX -= 1;
           }
           if (tid == 22){
               startY = startY-2;
               startX -= 1;
               endX -= 2;  
           }
           if (tid == 21){
               startY = startY-10;
           }
           if (tid == 20){
               startY = startY-10;
           }
           if (tid == 19){
               startY = startY-10;
               startX -=  1; 
           }
           if (tid == 18){
               startY = startY-10;
           }
           if (tid == 17){
               startY = startY-10;
           }

           endY = startY+10;
           points = [{
               x: startX, y: startY
           },{
              x: endX, y: startY
           },{
              x: endX+3, y: startY+8
           },{
              x: startX-3, y: startY+8
            }];
            d3.select("#svg").append("g").attr("id","drawing_"+tid)
            line = d3.line()
              .x(function(d) {
                 return d.x;
              })
              .y(function(d) {
                 return d.y;
            });
            d3.select("#drawing_"+tid).append("path").attr("d", line(points) + 'Z').style("fill", "red")
       }
       if (tid == "K" || tid == "L" || tid == "M" || tid == "N" || tid == "O" || tid == "P" || tid == "Q" || tid == "R" || tid == "S" || tid == "T"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           bbox1a = bbox1-1;
           startX = bbox1.x+3; 
           endX = bbox1.x+bbox1.width-2;
           startY = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
           startY = startY - bbox2.height;
           bbox3 = d3.select('[rel="'+tid+'A"]').node().getBBox();
           startY = startY - bbox3.height;
           if (tid == "K"){
               startY = startY-12;
               startX -= 1;
               endX -= 1;
           } 
           if (tid == "L"){
               startY = startY-10;
               startX -= 1;
               endX -= 1;
           } 
           if (tid == "M"){
               startY = startY-2;
           } 
           if (tid == "N"){
               startY = startY-3;
               startX -= 1
           } 
           if (tid == "O"){
               startY = startY+2;
               startX -= 1;
           } 
           if (tid == "P"){
               startY = startY+3;
           } 
           if (tid == "Q"){
               startY = startY-5;
               startX -= 1;
               endX = endX - 4;
           } 
           if (tid == "R"){
               startY = startY+2;
               startX -= 1;
           }
           if (tid == "S"){
               startY = startY-10;
               startX -= 1;
               endX -= 1;
           }
           if (tid == "T"){
               startY = startY-9;
               startX -= 1;
               endX -= 4;
           }
           endY = startY+10;
           points = [{
               x: startX, y: startY
           },{
              x: endX, y: startY
           },{
              x: endX+3, y: startY+8
           },{
              x: startX-3, y: startY+8
            }];
            d3.select("#svg").append("g").attr("id","drawing_"+tid)
            line = d3.line()
              .x(function(d) {
                 return d.x;
              })
              .y(function(d) {
                 return d.y;
            });
            d3.select("#drawing_"+tid).append("path").attr("d", line(points) + 'Z').style("fill", "red")
       }

   }

    topfound = false;
    if (operation.toUpperCase().indexOf(";;BUCCAL;;") > -1 && restoration_top_buccal.indexOf(";"+tid+";") > -1){
        topfound = true;
        if (includes[category]){
            if (includes[category][surface]){
                for (ioper = 0; ioper < includes[category][surface].length; ioper++){
                     if (";;"+includes[category][surface][ioper].name.toUpperCase()+";;" == ";;BUCCAL;;"){
                         includes[category][surface][ioper].included = true;   
                     }  
                }
           } 
       }  
    }
    if (operation.toUpperCase().indexOf(";;LABIALL;;") > -1 && restoration_top_labial.indexOf(";"+tid+";") > -1){
        topfound = true;
        if (includes[category]){
            if (includes[category][surface]){
                for (ioper = 0; ioper < includes[category][surface].length; ioper++){
                     if (";;"+includes[category][surface][ioper].name.toUpperCase()+";;" == ";;LABIALL;;"){
                         includes[category][surface][ioper].included = true;   
                     }  
                }
           } 
       }  
    }
    if (operation.toUpperCase().indexOf(";;LINGUAL;;") > -1 && restoration_top_lingual.indexOf(";"+tid+";") > -1){
        topfound = true;
        if (includes[category]){
            if (includes[category][surface]){
                for (ioper = 0; ioper < includes[category][surface].length; ioper++){
                     if (";;"+includes[category][surface][ioper].name.toUpperCase()+";;" == ";;LINGUAL;;"){
                         includes[category][surface][ioper].included = true;   
                     }  
                }
           } 
       }  
    }


    if (topfound){   
       if (parseFloat(tid) < 17 ){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
       if (tid == "A" || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I" || tid == "J"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
       if (parseFloat(tid) > 16 && parseFloat(tid) < 33){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
       if (tid == "K" || tid == "L" || tid == "M" || tid == "N" || tid == "O" || tid == "P" || tid == "Q" || tid == "R" || tid == "S" || tid == "T"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+4;
           newy = y;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
   }
    rightfound = false;
    if (operation.toUpperCase().indexOf(";;MESIAL;;") > -1 && restoration_right_mesial.indexOf(";"+tid+";") > -1){
        rightfound = true;
        if (includes[category]){
            if (includes[category][surface]){
                for (ioper = 0; ioper < includes[category][surface].length; ioper++){
                     if (";;"+includes[category][surface][ioper].name.toUpperCase()+";;" == ";;MESIAL;;"){
                         includes[category][surface][ioper].included = true;   
                     }  
                }
           } 
        }  
    }
    if (operation.toUpperCase().indexOf(";;DISTAL;;") > -1 && restoration_right_distal.indexOf(";"+tid+";") > -1){
        rightfound = true;
        if (includes[category]){
            if (includes[category][surface]){
                for (ioper = 0; ioper < includes[category][surface].length; ioper++){
                     if (";;"+includes[category][surface][ioper].name.toUpperCase()+";;" == ";;DISTAL;;"){
                         includes[category][surface][ioper].included = true;   
                     }  
                }
            } 
        }  
    }



   if (rightfound){
       if (parseFloat(tid) < 17){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*3)-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height+eheight;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
       if (tid == "A" || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I" || tid == "J"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*3)-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height+eheight;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
       if (parseFloat(tid) > 16 && parseFloat(tid) < 33){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*3)-4;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y+eheight;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
       if (tid == "K" || tid == "L" || tid == "M" || tid == "N" || tid == "O" || tid == "P" || tid == "Q" || tid == "R" || tid == "S" || tid == "T"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*3)-4;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y+eheight;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
   }

    bottomfound = false;
    if (operation.toUpperCase().indexOf(";;BUCCAL;;") > -1 && restoration_bottom_buccal.indexOf(";"+tid+";") > -1){
        bottomfound = true;
        if (includes[category]){
            if (includes[category][surface]){
                for (ioper = 0; ioper < includes[category][surface].length; ioper++){
                     if (";;"+includes[category][surface][ioper].name.toUpperCase()+";;" == ";;BUCCAL;;"){
                         includes[category][surface][ioper].included = true;   
                     }  
                }
            } 
        }  
    }
    if (operation.toUpperCase().indexOf(";;LABIAL;;") > -1 && restoration_bottom_labial.indexOf(";"+tid+";") > -1){
        bottomfound = true;
        if (includes[category]){
            if (includes[category][surface]){
                for (ioper = 0; ioper < includes[category][surface].length; ioper++){
                     if (";;"+includes[category][surface][ioper].name.toUpperCase()+";;" == ";;LABIALL;;"){
                         includes[category][surface][ioper].included = true;   
                     }  
                }
            } 
        }  
    }
    if (operation.toUpperCase().indexOf(";;PALATAL;;") > -1 && restoration_bottom_palatal.indexOf(";"+tid+";") > -1){
        bottomfound = true;
        if (includes[category]){
            if (includes[category][surface]){
                for (ioper = 0; ioper < includes[category][surface].length; ioper++){
                     if (";;"+includes[category][surface][ioper].name.toUpperCase()+";;" == ";;PALATAL;;"){
                         includes[category][surface][ioper].included = true;   
                     }  
                }
            } 
        }  
    }

   if (bottomfound){
       if (parseFloat(tid) < 17){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height+(eheight * 2);
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
       if (tid == "A" || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I" || tid == "J"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height+(eheight * 2);
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
       if (parseFloat(tid) > 16 && parseFloat(tid) < 33){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y+(eheight * 2);
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
       if (tid == "K" || tid == "L" || tid == "M" || tid == "N" || tid == "O" || tid == "P" || tid == "Q" || tid == "R" || tid == "S" || tid == "T"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y+(eheight * 2);
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
   }

    leftfound = false;
    if (operation.toUpperCase().indexOf(";;DISTAL;;") > -1 && restoration_left_distal.indexOf(";"+tid+";") > -1){
        leftfound = true;
        if (includes[category]){
            if (includes[category][surface]){
                for (ioper = 0; ioper < includes[category][surface].length; ioper++){
                     if (";;"+includes[category][surface][ioper].name.toUpperCase()+";;" == ";;DISTAL;;"){
                         includes[category][surface][ioper].included = true;   
                     }  
                }
            } 
        }  
    }
    if (operation.toUpperCase().indexOf(";;MESIAL;;") > -1 && restoration_left_mesial.indexOf(";"+tid+";") > -1){
        leftfound = true;
        if (includes[category]){
            if (includes[category][surface]){
                for (ioper = 0; ioper < includes[category][surface].length; ioper++){
                     if (";;"+includes[category][surface][ioper].name.toUpperCase()+";;" == ";;MESIAL;;"){
                         includes[category][surface][ioper].included = true;   
                     }  
                }
            } 
        }  
    }


   if (leftfound){
       if (parseFloat(tid) < 17){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+ewidth-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height+eheight;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
       if (tid == "A" || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I" || tid == "J"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+ewidth-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height+eheight;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
       if (parseFloat(tid) > 16 && parseFloat(tid) < 33){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+ewidth-3;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y+eheight; 
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
       if (tid == "K" || tid == "L" || tid == "M" || tid == "N" || tid == "O" || tid == "P" || tid == "Q" || tid == "R" || tid == "S" || tid == "T"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+ewidth-3;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y+eheight; 
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",newx)
             .attr("cy",newy)
             .attr("r",r)
             .attr("fill","red") 
       }
   }

    middlefound = false;
    if (operation.toUpperCase().indexOf(";;OCCLUSAL;;") > -1 && restoration_middle_occlusal.indexOf(";"+tid+";") > -1){
        middlefound = true;
        if (includes[category]){
            if (includes[category][surface]){
                for (ioper = 0; ioper < includes[category][surface].length; ioper++){
                     if (";;"+includes[category][surface][ioper].name.toUpperCase()+";;" == ";;OCCLUSAL;;"){
                         includes[category][surface][ioper].included = true;   
                     }  
                }
            } 
        }  
    }
    if (operation.toUpperCase().indexOf(";;INCISAL;;") > -1 && restoration_middle_incisal.indexOf(";"+tid+";") > -1){
        middlefound = true;
        if (includes[category]){
            if (includes[category][surface]){
                for (ioper = 0; ioper < includes[category][surface].length; ioper++){
                     if (";;"+includes[category][surface][ioper].name.toUpperCase()+";;" == ";;INCISAL;;"){
                         includes[category][surface][ioper].included = true;   
                     }  
                }
            } 
        }  
    }



   if (middlefound){
       if (parseFloat(tid) < 17){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+ewidth-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height+eheight;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           leftcenter = newx+r
           cx = leftcenter+r;
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*3)-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height+eheight;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           rightcenter = newx+r;
           rx = rightcenter-leftcenter
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           topcenter = newy+r;
           cy = topcenter+r-3;
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height+(eheight * 2);
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           bottomcenter = newy+r 
           ry = bottomcenter-topcenter;
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           rx = rx/1.2
           ry = ry/1.2
           d3.select("#drawing_"+tid).append("ellipse").style("stroke","red")
             .attr("cx",cx)
             .attr("cy",cy)
             .attr("rx",rx/2)
             .attr("ry",ry/2)
             .attr("fill","red") 
       }
       if (tid == "A" || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I" || tid == "J"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+ewidth-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height+eheight;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           leftcenter = newx+r
           cx = leftcenter+r;
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*3)-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height+eheight;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           rightcenter = newx+r;
           rx = rightcenter-leftcenter
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           topcenter = newy+r;
           cy = topcenter+r-3;
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y-bbox2.height+(eheight * 2);
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           bottomcenter = newy+r 
           ry = bottomcenter-topcenter;
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           rx = rx/1.2
           ry = ry/1.2
           d3.select("#drawing_"+tid).append("ellipse").style("stroke","red")
             .attr("cx",cx)
             .attr("cy",cy)
             .attr("rx",rx/2)
             .attr("ry",ry/2)
             .attr("fill","red") 
       }
       if (parseFloat(tid) > 16 && parseFloat(tid) < 33){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+ewidth-3;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y+eheight; 
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           leftcenter = newx+r
           cx = leftcenter+r;
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*3)-4;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y+eheight;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           rightcenter = newx+r;
           rx = rightcenter-leftcenter
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           topcenter = newy+r;
           cy = topcenter+r-3;
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y+(eheight * 2);
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           bottomcenter = newy+r 
           ry = bottomcenter-topcenter;
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           rx = rx/1.2
           ry = ry/1.2
           d3.select("#drawing_"+tid).append("ellipse").style("stroke","red")
             .attr("cx",cx)
             .attr("cy",cy)
             .attr("rx",rx/2)
             .attr("ry",ry/2)
             .attr("fill","red")  
       } 
       if (tid == "K" || tid == "L" || tid == "M" || tid == "N" || tid == "O" || tid == "P" || tid == "Q" || tid == "R" || tid == "S" || tid == "T"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+ewidth-3;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y+eheight; 
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           leftcenter = newx+r
           cx = leftcenter+r;
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*3)-4;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y+eheight;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           rightcenter = newx+r;
           rx = rightcenter-leftcenter
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y;
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           topcenter = newy+r;
           cy = topcenter+r-3;
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           ewidth = bbox1.width/3
           newx = bbox1.x+(ewidth*2)-3;
           y = bbox1.y+4;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           eheight = bbox2.height/3
           newy = y+(eheight * 2);
           if (ewidth <= eheight){
               r = ewidth/1.5;
           }else{
               r = eheight/1.5;
           }    
           bottomcenter = newy+r 
           ry = bottomcenter-topcenter;
           if (d3.select("#drawing_"+tid).length == 0){ 
               d3.select("#svg").append("g").attr("id","drawing_"+tid)
           } 
           rx = rx/1.2
           ry = ry/1.2
           d3.select("#drawing_"+tid).append("ellipse").style("stroke","red")
             .attr("cx",cx)
             .attr("cy",cy)
             .attr("rx",rx/2)
             .attr("ry",ry/2)
             .attr("fill","red")  
       } 
   }



   if (operation.toUpperCase() == "CLASS1"){
       if (parseFloat(tid) < 17){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x = (bbox1.x+(bbox1.width/1.5));
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           centerX = x;
           centerY = y-(bbox2.height/2);
           circleradius = 4;
           centerX = centerX - circleradius;
           centerY = centerY - circleradius;
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",centerX)
             .attr("cy",centerY)
             .attr("r",circleradius)
       } 
       if (tid == "A" || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x = (bbox1.x+(bbox1.width/1.5));
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           centerX = x;
           centerY = y-(bbox2.height/2);
           circleradius = 4;
           centerX = centerX - circleradius;
           centerY = centerY - circleradius;
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",centerX)
             .attr("cy",centerY)
             .attr("r",circleradius)
       } 
       if (parseFloat(tid) > 16){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x = (bbox1.x+(bbox1.width/1.5));
           y = bbox1.y;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           centerX = x;
           centerY = y+(bbox2.height/1.5);
           circleradius = 4;
           centerX = centerX - circleradius;
           centerY = centerY - circleradius;
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",centerX)
             .attr("cy",centerY)
             .attr("r",circleradius)
       }
       if (tid == "K" || tid == "L" || tid == "M" || tid == "N" || tid == "O" || tid == "P" || tid == "Q" || tid == "R" || tid == "S" || tid == "T"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x = (bbox1.x+(bbox1.width/1.5));
           y = bbox1.y;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           centerX = x;
           centerY = y+(bbox2.height/1.5);
           circleradius = 4;
           centerX = centerX - circleradius;
           centerY = centerY - circleradius;
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",centerX)
             .attr("cy",centerY)
             .attr("r",circleradius)
       }
   }
   if (operation.toUpperCase() == "CLASS2"){
       if (tid < 17){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x = (bbox1.x+(bbox1.width/1.5));
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           centerX = x;
           centerY = y-(bbox2.height/2);
           circleradius = (bbox2.width/3)-1;
           centerX = centerX - circleradius;
           centerY = centerY - circleradius+2;
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",centerX)
             .attr("cy",centerY)
             .attr("r",circleradius)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",centerX+(circleradius/1.2))
             .attr("cy",centerY)
             .attr("r",circleradius)
       } 
       if (tid == "A" || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x = (bbox1.x+(bbox1.width/1.5));
           y = bbox1.y+bbox1.height;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           centerX = x;
           centerY = y-(bbox2.height/2);
           circleradius = (bbox2.width/3)-1;
           centerX = centerX - circleradius;
           centerY = centerY - circleradius+2;
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",centerX)
             .attr("cy",centerY)
             .attr("r",circleradius)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",centerX+(circleradius/1.2))
             .attr("cy",centerY)
             .attr("r",circleradius)
       } 
       if (tid > 16){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x = (bbox1.x+(bbox1.width/1.5));
           y = bbox1.y;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           centerX = x;
           centerY = y+(bbox2.height/1.5);
           circleradius = (bbox2.width/3)-1;
           centerX = centerX - circleradius;
           centerY = centerY - circleradius+2;
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",centerX)
             .attr("cy",centerY)
             .attr("r",circleradius)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",centerX+(circleradius/1.2))
             .attr("cy",centerY)
             .attr("r",circleradius)
       }
       if (tid == "K" || tid == "L" || tid == "M" || tid == "N" || tid == "O" || tid == "P" || tid == "Q" || tid == "R" || tid == "S" || tid == "T"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x = (bbox1.x+(bbox1.width/1.5));
           y = bbox1.y;
           bbox2 = d3.select('[rel="'+tid+'B"]').node().getBBox();
           centerX = x;
           centerY = y+(bbox2.height/1.5);
           circleradius = (bbox2.width/3)-1;
           centerX = centerX - circleradius;
           centerY = centerY - circleradius+2;
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",centerX)
             .attr("cy",centerY)
             .attr("r",circleradius)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",centerX+(circleradius/1.2))
             .attr("cy",centerY)
             .attr("r",circleradius)
       }
   }



   if (operation.toUpperCase() == "DIESTEMA"){
       if (tid < 16){
           tid1 = parseFloat(tid)+1
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x1 = bbox1.x;
           y1 = bbox1.y;
           width1 = bbox1.width;
           height1 = bbox1.height;  
           bbox2 = d3.select('[rel="'+tid1+'T"]').node().getBBox();
           x2 = bbox2.x;
           y2 = bbox2.y;
           wdiff = (x2-(x1+width1))/2
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
             .attr("x1",x1+width1+wdiff-3)
             .attr("y1",y1)
             .attr("x2",x1+width1+wdiff-3)
             .attr("y2",y1+height1);    
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
             .attr("x1",x1+width1+wdiff+2)
             .attr("y1",y1)
             .attr("x2",x1+width1+wdiff+2)
             .attr("y2",y1+height1);   
       }
       if (tid > 17){
           tid1 = parseFloat(tid)+1
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x1 = bbox1.x;
           y1 = bbox1.y;
           width1 = bbox1.width;
           height1 = bbox1.height;  
           bbox2 = d3.select('[rel="'+tid1+'T"]').node().getBBox();
           x2 = bbox2.x;
           y2 = bbox2.y;
           wdiff = (x2-(x1+width1))/2
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
             .attr("x1",x1+width1+wdiff-3)
             .attr("y1",y1)
             .attr("x2",x1+width1+wdiff-3)
             .attr("y2",y1+height1);    
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
             .attr("x1",x1+width1+wdiff+2)
             .attr("y1",y1)
             .attr("x2",x1+width1+wdiff+2)
             .attr("y2",y1+height1);   
       }
       if (tid == "A" || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I"){
           if (tid == "A"){
               tid1 = "B";
           } 
           if (tid == "B"){
               tid1 = "C";
           } 
           if (tid == "C"){
               tid1 = "D";
           } 
           if (tid == "D"){
               tid1 = "E";
           } 
           if (tid == "E"){
               tid1 = "F";
           } 
           if (tid == "F"){
               tid1 = "G";
           } 
           if (tid == "G"){
               tid1 = "H";
           } 
           if (tid == "H"){
               tid1 = "I";
           } 
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x1 = bbox1.x;
           y1 = bbox1.y;
           width1 = bbox1.width;
           height1 = bbox1.height;  
           bbox2 = d3.select('[rel="'+tid1+'T"]').node().getBBox();
           x2 = bbox2.x;
           y2 = bbox2.y; 
           wdiff = (x2-(x1+width1))/2
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
             .attr("x1",x1+width1+wdiff-3)
             .attr("y1",y1)
             .attr("x2",x1+width1+wdiff-3)
             .attr("y2",y1+height1);    
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
             .attr("x1",x1+width1+wdiff+2)
             .attr("y1",y1)
             .attr("x2",x1+width1+wdiff+2)
             .attr("y2",y1+height1);  
       }
       if (tid == "K" || tid == "L" || tid == "M" || tid == "N" || tid == "O" || tid == "P" || tid == "Q" || tid == "R" || tid == "S" || tid == "T"){
           if (tid == "T"){
               tid1 = "S";
           } 
           if (tid == "S"){
               tid1 = "R";
           } 
           if (tid == "R"){
               tid1 = "Q";
           } 
           if (tid == "Q"){
               tid1 = "P";
           } 
           if (tid == "P"){
               tid1 = "O";
           } 
           if (tid == "O"){
               tid1 = "N";
           } 
           if (tid == "N"){
               tid1 = "M";
           } 
           if (tid == "M"){
               tid1 = "L";
           } 
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           x1 = bbox1.x;
           y1 = bbox1.y;
           width1 = bbox1.width;
           height1 = bbox1.height;  
           bbox2 = d3.select('[rel="'+tid1+'T"]').node().getBBox();
           x2 = bbox2.x;
           y2 = bbox2.y;  
           wdiff = (x2-(x1+width1))/2
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
             .attr("x1",x1+width1+wdiff-3)
             .attr("y1",y1)
             .attr("x2",x1+width1+wdiff-3)
             .attr("y2",y1+height1);    
           d3.select("#drawing_"+tid).append("line").style("stroke","red")
             .attr("x1",x1+width1+wdiff+2)
             .attr("y1",y1)
             .attr("x2",x1+width1+wdiff+2)
             .attr("y2",y1+height1);  
       }
   } 


   if (operation.toUpperCase() == "PERIAPICALABCESS"){
       bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
       x = bbox1.x;
       y = bbox1.y;
       width = bbox1.width;
       height = bbox1.height;
       if (parseInt(tid) > 0 && parseInt(tid) < 17){
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","none")
             .attr("cx",x+(width/2)+2)
             .attr("cy",y+(10/2))
             .attr("r",(10/2))
       }          
       if (parseInt(tid) > 16 && parseInt(tid) < 33){
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","none")
             .attr("cx",x+(width/2)+2)
             .attr("cy",y+height)
             .attr("r",(10/2))
       } 
       if (tid == "A" || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I" || tid == "J"){
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","none")
             .attr("cx",x+(width/2)+2)
             .attr("cy",y+(10/2))
             .attr("r",(10/2))
       }
       if (tid == "K" || tid == "L" || tid == "M" || tid == "N" || tid == "O" || tid == "P" || tid == "Q" || tid == "R" || tid == "S" || tid == "T"){
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","none")
             .attr("cx",x+(width/2)+2)
             .attr("cy",y+height)
             .attr("r",(10/2))
       }
   }
   if (operation.toUpperCase() == "POSTANDCORE"){
       if (parseInt(tid) > 0 && parseInt(tid) < 17){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x + (bbox1.width/2) ;
           endX = (bbox1.x+(bbox1.width/3))+2;
           startY = bbox1.y+(bbox1.height/3);
           endY = bbox1.y+5;
           path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY+2, endX+(bbox1.width/3), endY,endX, endY);
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("path").attr("d",path).style("fill","none").style("stroke","red");
           bbox1 = d3.select('[rel="'+tid+'T"]').select('[rel="CR2"]').node().getBBox();
           x = startX;
           y = startY;
           width = bbox1.width;
           height = bbox1.height;
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",startX)
             .attr("cy",startY+5)
             .attr("r",(6/2))
           d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').attr("ostroke",d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').attr("stroke"));
           d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').attr("ostrokewidth",d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').attr("stroke-width"));
           d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').style("stroke","red");
           d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').attr("stroke","red");
           d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').attr("stroke-width","1");
       }   
       if (parseInt(tid) > 16 && parseInt(tid) < 33){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           startX = bbox1.x + (bbox1.width/2) ;
           endX = (bbox1.x+bbox1.width);
           hgt = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
           startY = bbox1.y+bbox1.height-hgt.height-10;
           endY = bbox1.y+bbox1.height;
           path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY, endX-(bbox1.width/3)-5, endY,endX-5, endY-10);
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("path").attr("d",path).style("fill","none").style("stroke","red");
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",startX)
             .attr("cy",startY-3)
             .attr("r",(6/2))
           d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').style("stroke","red");
           d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').attr("stroke","red");
           d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').attr("stroke-width","1");
       } 
       if (tid == "A" || tid == "B" || tid == "C" || tid == "D" || tid == "E" || tid == "F" || tid == "G" || tid == "H" || tid == "I" || tid == "J"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           bbox1a = bbox1;
           startX = bbox1.x + (bbox1.width/2) ;
           endX = (bbox1.x+(bbox1.width/3))+2;
           startY = bbox1.y+(bbox1.height/3);
           endY = bbox1.y+5;
           path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY+2, endX+(bbox1.width/3), endY,endX, endY);
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("path").attr("d",path).style("fill","none").style("stroke","red");
           bbox1 = d3.select('[rel="'+tid+'T"]').select('[rel="CR2"]').node().getBBox();
           x = startX;
           y = startY;
           width = bbox1.width;
           height = bbox1.height;
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",startX)
             .attr("cy",startY+5)
             .attr("r",(6/2))
           d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').style("stroke","red");
           d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').attr("stroke","red");
           d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').attr("stroke-width","1");
       }
       if (tid == "K" || tid == "L" || tid == "M" || tid == "N" || tid == "O" || tid == "P" || tid == "Q" || tid == "R" || tid == "S" || tid == "T"){
           bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
           startX = bbox1.x + (bbox1.width/2) ;
           endX = (bbox1.x+bbox1.width);
           hgt = d3.select('[rel="'+tid+'T"]').select('[rel="'+tid+'"]').node().getBBox();
           startY = bbox1.y+bbox1.height-hgt.height-10;
           endY = bbox1.y+bbox1.height;
           path= this.interpolateQuadraticBezierCurve(0, 1, startX, startY, endX-(bbox1.width/3)-5, endY,endX-5, endY-10);
           d3.select("#svg").append("g").attr("id","drawing_"+tid)
           d3.select("#drawing_"+tid).append("path").attr("d",path).style("fill","none").style("stroke","red");
           d3.select("#drawing_"+tid).append("circle").style("stroke","red").style("fill","red")
             .attr("cx",startX)
             .attr("cy",startY-3)
             .attr("r",(6/2))
           d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').style("stroke","red");
           d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').attr("stroke","red");
           d3.select('[rel="'+tid+'A"]').select('[rel="CR2"]').attr("stroke-width","1");
       }
   }

   if (operation.toUpperCase() == "IMPACTEDTOOTH"){
       bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
       x = bbox1.x;
       y = bbox1.y;
       width = bbox1.width;
       height = bbox1.height;
       d3.select("#svg").append("g").attr("id","drawing_"+tid)
       d3.select("#drawing_"+tid).append("ellipse").style("stroke","red").style("fill","none")
         .attr("cx",x+(width/2))
         .attr("cy",y+(height/2))
         .attr("rx",(width/2))
         .attr("ry",(height/2))
   }   
   if (operation.toUpperCase() == "DRIFTING"){
       d3.select("#drawing_"+tid).remove();
       d3.select("#"+mastersvg).select("#svg").select("g").append("g").attr("id","drawing_"+tid).append("g");
       bbox = d3.select('[rel="'+tid+'G"]').node().getBBox()      //.getBBox();
       startX = bbox.x+(bbox.width/2);
       endX = bbox.x;
       startY = bbox.y+bbox.height;
       endY = bbox.y+bbox.height;
       let newpos = this.getadjust("drifting",parseInt(tid));
       d3.select("#drawing_"+tid).select("g").attr("transform","translate("+newpos.x+","+newpos.y+") scale("+newpos.scalex+","+newpos.scaley+")").append("line")
              .attr("x1",startX)
              .attr("y1",startY)
              .attr("x2",endX)
              .attr("y2",endY)
              .attr("stroke-width", newpos.width)
              .attr("stroke", "red")
              .attr("marker-end", "url(#arrow)")

   }

   if (operation.toUpperCase() == "CROWN"){
       bbox1 = d3.select('[rel="'+tid+'A"]').node().getBoundingClientRect();
       bbox2 = d3.select('[rel="'+tid+'B"]').node().getBoundingClientRect();
       d3.select("#svg").select("g").append("g").attr("id","drawing_A_"+tid).attr("viewBox",d3.select('[rel="'+tid+'A"]').attr("viewBox"));
       d3.select("#svg").select("g").append("g").attr("id","drawing_B_"+tid).attr("viewBox",d3.select('[rel="'+tid+'B"]').attr("viewBox"));
       d3.select("#drawing_A_"+tid).append("path").attr("d",d3.select('[rel="'+tid+'A"]').select("path").attr("d")).style("fill","red").style("stroke","red")
       d3.select("#drawing_B_"+tid).append("path").attr("d",d3.select('[rel="'+tid+'B"]').select("path").attr("d")).style("fill","red").style("stroke","red")
   }   

   if (operation.toUpperCase() == "CROWNDARK"){
       bbox1 = d3.select('[rel="'+tid+'A"]').node().getBoundingClientRect();
       bbox2 = d3.select('[rel="'+tid+'B"]').node().getBoundingClientRect();
       d3.select("#svg").append("svg").attr("id","drawing_A_"+tid).attr("viewBox",d3.select('[rel="'+tid+'A"]').attr("viewBox"))
//       d3.select("#drawing_A_"+tid).append("path").attr("d",d3.select('[rel="'+tid+'A"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
       d3.select("#drawing_A_"+tid).append("path").attr("d",d3.select('[rel="'+tid+'A"]').select("path").attr("d")).style("fill","red").style("stroke","red")
       d3.select("#svg").append("svg").attr("id","drawing_B_"+tid).attr("viewBox",d3.select('[rel="'+tid+'B"]').attr("viewBox"))
//       d3.select("#drawing_B_"+tid).append("path").attr("d",d3.select('[rel="'+tid+'B"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
       d3.select("#drawing_B_"+tid).append("path").attr("d",d3.select('[rel="'+tid+'B"]').select("path").attr("d")).style("fill","red").style("stroke","red")
   }
   if (operation.toUpperCase() == "CROWNLIGHT"){
       bbox1 = d3.select('[rel="'+tid+'A"]').node().getBoundingClientRect();
       bbox2 = d3.select('[rel="'+tid+'B"]').node().getBoundingClientRect();
       d3.select("#svg").append("svg").attr("id","drawing_A_"+tid).attr("viewBox",d3.select('[rel="'+tid+'A"]').attr("viewBox"))
//       d3.select("#drawing_A_"+tid).append("path").attr("d",d3.select('[rel="'+tid+'A"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
       d3.select("#drawing_A_"+tid).append("path").attr("d",d3.select('[rel="'+tid+'A"]').select("path").attr("d")).style("fill","red").style("stroke","red").style("stroke-opacity",".5").style("fill-opacity",".5")
       d3.select("#svg").append("svg").attr("id","drawing_B_"+tid).attr("viewBox",d3.select('[rel="'+tid+'B"]').attr("viewBox"))
//       d3.select("#drawing_B_"+tid).append("path").attr("d",d3.select('[rel="'+tid+'B"]').select("path").attr("d")).style("mask","url(#mask-stripe)").style("fill","red")
       d3.select("#drawing_B_"+tid).append("path").attr("d",d3.select('[rel="'+tid+'B"]').select("path").attr("d")).style("fill","red").style("stroke","red").style("stroke-opacity",".5").style("fill-opacity",".5")
   }

   if (operation.toUpperCase() == "EXTRACTION"){
       bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
       x = bbox1.x;
       y = bbox1.y;
       width = bbox1.width;
       height = bbox1.height;
       d3.select("#svg").append("g").attr("id","drawing_"+tid)
       d3.select("#drawing_"+tid).append("line").style("stroke","red")
         .attr("x1",x+width)
         .attr("y1",y)
         .attr("x2",x)
         .attr("y2",y+height);
   }
   if (operation.toUpperCase() == "MISSINGTOOTH"){
       bbox1 = d3.select('[rel="'+tid+'T"]').node().getBBox();
       x = bbox1.x;
       y = bbox1.y;
       width = bbox1.width;
       height = bbox1.height;
       d3.select("#svg").append("g").attr("id","drawing_"+tid)
       d3.select("#drawing_"+tid).append("line").style("stroke","red")
         .attr("x1",x)
         .attr("y1",y)
         .attr("x2",x+width)
         .attr("y2",y+height)
       d3.select("#drawing_"+tid).append("line").style("stroke","red")
         .attr("x1",x+width)
         .attr("y1",y)
         .attr("x2",x)
         .attr("y2",y+height);


//       bbox1 = d3.select('[rel="'+tid+'"]').node().getClientRects()[0];
//       bbox2 = d3.select('[rel="'+tid+'A"]').node().getClientRects()[0];
//       bbox3 = d3.select('[rel="'+tid+'B"]').node().getClientRects()[0];
//       width = bbox1.width;
//       if (bbox2.width > width){
//           width = bbox2.width;
//       }     
//       if (bbox3.width > width){
//           width = bbox3.width;
//       } 
//       width = width
//       x = bbox1.x
 //      if (bbox2.x < x){
//           x = bbox2.x;
//       }     
//       if (bbox3.x < x){
//           x = bbox3.x;
//       } 
//       y = bbox1.y
//       if (bbox2.y < y){
//           y = bbox2.y;
//       }     
//       if (bbox3.y < y){
//           y = bbox3.y;
//       } 
//       height = bbox3.y+(bbox3.height);
//       d3.select("#svg").append("svg").attr("id","drawing_"+tid).attr("viewBox","555 70 30 800")
//         .attr("viewBox",x+" "+y+" "+(width*2)+" "+(height*4))  
//         .attr("x","-40")    //-1*35
//         .attr("y","0")
//         .attr("x",x)
//         .attr("y",y)
//         .attr("width",width)
//         .attr("height",height)
//       d3.select("body").append("svg").attr("id","drawing_"+tid).attr("y",y)
//       d3.select("#svg").append("g").attr("id","drawing_"+tid)
//       d3.select("#drawing_"+tid).append("line").style("stroke","red")
//         .attr("x1",x)
//         .attr("y1",y)
//         .attr("x2",x+width)
//         .attr("y2",height)
//       d3.select("#drawing_"+tid).append("line").style("stroke","red")
//         .attr("x1",x+width)
//         .attr("y1",y)
//         .attr("x2",x)
//         .attr("y2",height);
//       newx = parseFloat(d3.select("#drawing_"+tid).attr("x"));
//       newx = newx + diff;
//x = d3.select('[rel="'+tid+'"]').node().getBBox().x
//       d3.select("#drawing_"+tid).attr("x",x);
//       nbox = d3.select("#drawing_"+tid).node().getBoundingClientRect();
//       nwidth = nbox.left+nbox.width;
//       diff = (x+width) - nwidth;
//       diff = (x+width)  - nwidth;
//       diff = x - nbox.left;
//       diff = diff/2   
//       newx = -30 + diff 
//      d3.select("#drawing_"+tid).attr("transform", "translate("+diff+",-100) scale(.5,1)")
   }
   if (category.toUpperCase() == "RESTORATION"){
       for (tskey in dentaldata["Restoration"]){ 
            for (tsskey in dentaldata["Restoration"][tskey]){ 
                 fteeth = [];
                 for (idental = 0; idental < dentaldata["Restoration"][tskey][tsskey].length; idental++){
                      if (dentaldata["Restoration"][tskey][tsskey][idental] == tid){
                          if (includes[category]){
                              if (includes[category][tskey]){
                                  for (ioper = 0; ioper < includes[category][tskey].length; ioper++){
                                       if (includes[category][tskey][ioper].name.toUpperCase() == tsskey.toUpperCase()){
                                           if (includes[category][tskey][ioper].included){
                                               fteeth.push(tid);
                                           } 
                                       } 
                                  }
                              }
                          }    
                      }else{
                          fteeth.push(dentaldata["Restoration"][tskey][tsskey][idental]);
                      }  
                 }
                 dentaldata["Restoration"][tskey][tsskey] = fteeth;
            }
       } 
       ndentaldata = {};
       dentaldatafound = false;  
       for (tskey in dentaldata["Restoration"]){ 
            for (tsskey in dentaldata["Restoration"][tskey]){ 
                 if (dentaldata["Restoration"][tskey][tsskey].length > 0){
                     dentaldatafound = true;  
                     if (!ndentaldata["Restoration"]){
                         ndentaldata["Restoration"] = {};
                     }
                     if (!ndentaldata["Restoration"][tskey]){
                         ndentaldata["Restoration"][tskey] = {};
                     }
                     if (!ndentaldata["Restoration"][tskey][tsskey]){
                         ndentaldata["Restoration"][tskey][tsskey] = [];
                     }
                     ndentaldata["Restoration"][tskey][tsskey] = dentaldata["Restoration"][tskey][tsskey];
                 }
            } 
       } 
       if (!dentaldatafound){
           ndentaldata = {};
           for (tkey in dentaldata){ 
                if (tkey.toUpperCase() == "RESTORATION"){
                    continue;
                }
                ndentaldata[tkey] = dentaldata[tkey];
           }            
           dentaldata = ndentaldata;  
       }else{
           for (tkey in dentaldata){ 
                if (tkey.toUpperCase() == "RESTORATION"){
                    dentaldata[tkey] = ndentaldata[tkey];
                }
           }            
       }  
   }

   if (d3.select("#drawing_"+tid).length == 0 ){
       if (d3.select("#drawing_A_"+tid).length != 0 || d3.select("#drawing_B_"+tid).length != 0){
           nselectedtooth = {};      
       }else{
          d3.select('[tid="t_'+tid+'"]').attr("stroke",null);
          d3.select('[tid="t_'+tid+'"]').attr("fill",null);
          nselectedtooth = {};
          for (skey in selectedtooth){
               sk = skey.split("_")[1] 
               if (sk == tid){
                   continue;
               }
               nselectedtooth[skey] = selectedtooth[skey];
          } 
          ndentaldata  = {};
          for (tkey in dentaldata){
               childkey = false; 
               for (tskey in dentaldata[tkey]){
                    if (typeof dentaldata[tkey][tskey] == "object"){  
                        childkey = true; 
                    } 
               }
               if (!childkey){
                   if (dentaldata[tkey] && dentaldata[tkey].length == 0){
                       continue;
                   } 
                   ndentaldata[tkey] = []; 
                   for (idental = 0; idental < dentaldata[tkey].length; idental++){
                        if (dentaldata[tkey][idental] == tid){
                            continue;
                        } 
                        ndentaldata[tkey].push(dentaldata[tkey][idental]);
                   } 
               }else{
                   for (tskey in dentaldata[tkey]){
                        if (tkey.toUpperCase() == "RESTORATION"){
                            for (tsskey in dentaldata[tkey][tskey]){
                                 for (idental = 0; idental < dentaldata[tkey][tskey][tsskey].length; idental++){
                                      if (dentaldata[tkey][tskey][tsskey][idental] == tid){
                                          continue;
                                      } 
                                      if (!ndentaldata[tkey]){
                                          ndentaldata[tkey] = {};
                                      }
                                      if (!ndentaldata[tkey][tskey]){
                                          ndentaldata[tkey][tskey] = {};
                                      }
                                      if (!ndentaldata[tkey][tskey][tsskey]){
                                          ndentaldata[tkey][tskey][tsskey] = [];
                                      }
                                      ndentaldata[tkey][tskey][tsskey].push(dentaldata[tkey][tskey][tsskey][idental]);
                                 } 
                            }
                            continue;
                        }
                        if (dentaldata[tkey][tskey] && dentaldata[tkey][tskey].length == 0){
                            continue;
                        }  
                        if (!ndentaldata[tkey]){
                            ndentaldata[tkey] = {};
                        }
                        if (!ndentaldata[tkey][tskey]){
                            ndentaldata[tkey][tskey] = []
                        }
//                        ndentaldata[tkey][tskey] = [];
                        for (idental = 0; idental < dentaldata[tkey][tskey].length; idental++){
                             if (dentaldata[tkey][tskey][idental] == tid){
                                 continue;
                             } 
                             ndentaldata[tkey][tskey].push(dentaldata[tkey][tskey][idental]);
                        } 
                   }
               }      
          }   
          dentaldata = ndentaldata;
          selectedtooth = nselectedtooth;
          ndentaldata  = {};
          for (tkey in dentaldata){
               childkey = false; 
               for (tskey in dentaldata[tkey]){
                    if (typeof dentaldata[tkey][tskey] == "object"){  
                        childkey = true; 
                    } 
               }
               if (!childkey){
                   if (dentaldata[tkey] && dentaldata[tkey].length == 0){
                       continue;
                   } 
                   ndentaldata[tkey] = []; 
                   for (idental = 0; idental < dentaldata[tkey].length; idental++){
                        ndentaldata[tkey].push(dentaldata[tkey][idental]);
                   } 
               }else{
                   for (tskey in dentaldata[tkey]){
                        if (tkey.toUpperCase() == "RESTORATION"){
                            for (tsskey in dentaldata[tkey][tskey]){
                                 for (idental = 0; idental < dentaldata[tkey][tskey][tsskey].length; idental++){
                                      if (dentaldata[tkey][tskey][tsskey][idental] == tid){
                                          continue;
                                      } 
                                      if (!ndentaldata[tkey]){
                                          ndentaldata[tkey] = {};
                                      }
                                      if (!ndentaldata[tkey][tskey]){
                                          ndentaldata[tkey][tskey] = {};
                                      }
                                      if (!ndentaldata[tkey][tskey][tsskey]){
                                          ndentaldata[tkey][tskey][tsskey] = [];
                                      }
                                      ndentaldata[tkey][tskey][tsskey].push(dentaldata[tkey][tskey][tsskey][idental]);
                                 } 
                            }
                            continue;
                        }    
                        if (dentaldata[tkey][tskey] && dentaldata[tkey][tskey].length == 0){
                            continue;
                        }  
                        if (!ndentaldata[tkey]){
                             ndentaldata[tkey] = {};
                        }
                        if (!ndentaldata[tkey][tskey]){
                             ndentaldata[tkey][tskey] = []
                        }
                        ndentaldata[tkey][tskey] = [];
                        for (idental = 0; idental < dentaldata[tkey][tskey].length; idental++){
                             ndentaldata[tkey][tskey].push(dentaldata[tkey][tskey][idental]);
                        } 
                   }
               }      
          }  
          dentaldata = ndentaldata;
          // generatedatafordbupdate();
        }  
   }       
},

 interpolateQuadraticBezierCurve : function(lambdaStart,lambdaEnd,xAnchorStart,yAnchorStart,xHandle,yHandle,xAnchorEnd,yAnchorEnd) {
          let x0, y0, x1, y1, txt;
          if (lambdaStart > 0.0) 
             {
              x0 =  xAnchorStart + lambdaStart * ( xHandle    - xAnchorStart );
              y0 =  yAnchorStart + lambdaStart * ( yHandle    - yAnchorStart );
              x1 =  xHandle      + lambdaStart * ( xAnchorEnd - xHandle      );
              y1 =  yHandle      + lambdaStart * ( yAnchorEnd - yHandle      );
              xAnchorStart = x0 + lambdaStart * ( x1 - x0 );
              yAnchorStart = y0 + lambdaStart * ( y1 - y0 );
              xHandle      = x1;
              yHandle      = y1;
             }

          if (lambdaEnd < 1.0) 
             {
              x0 =  xAnchorStart + lambdaEnd * ( xHandle    - xAnchorStart );
              y0 =  yAnchorStart + lambdaEnd * ( yHandle    - yAnchorStart );
              x1 =  xHandle      + lambdaEnd * ( xAnchorEnd - xHandle      );
              y1 =  yHandle      + lambdaEnd * ( yAnchorEnd - yHandle      );
              xHandle    = x0;
              yHandle    = y0;
              xAnchorEnd = x0 + lambdaEnd * ( x1 - x0 );
              yAnchorEnd = y0 + lambdaEnd * ( y1 - y0 );
             }
          txt  = 'M' + xAnchorStart + ' ' + yAnchorStart + ' ';
          txt += 'Q' + xHandle      + ' ' + yHandle      + ' ';
          txt +=       xAnchorEnd   + ' ' + yAnchorEnd;
          return txt;
         },
 //   },
    drawBox: function(obj,id,x,y,width,height){
        console.log(id);
        if (parseInt(id) < 50){
            if (d3.select("#svgmain").select("#svg").select("g").select("#coverbox")){
                d3.select("#svgmain").select("#svg").select("g").select("#coverbox").remove();
                if (id === selectedID){
                    selectedID = "";
                    mastersvg = ""; 
                    window.emitter.emit('selectedTeeth',selectedID) ;
                    return;
                }
            }
            selectedID = id;
            window.emitter.emit('selectedTeeth',selectedID)   
            mastersvg = "svgmain"; 
            d3.select("#svgmain").select("#svg").select("g").append("rect").attr("id","coverbox").attr("height",height).attr("width",width).attr("x",x).attr("y",y).style("stroke","yellow").style("stroke-width","2px").attr("fill","none");
        }else{
            if (d3.select("#svgchild").select("#svg").select("g").select("#coverbox")){
                d3.select("#svgchild").select("#svg").select("g").select("#coverbox").remove();
                if (id === selectedID){
                    selectedID = "";
                    mastersvg = ""; 
                    window.emitter.emit('selectedTeeth',selectedID);
                    return;
                }
            }
            selectedID = id;
            window.emitter.emit('selectedTeeth',selectedID)   
            mastersvg = "svgchild"
            d3.select("#svgchild").select("#svg").select("g").append("rect").attr("id","coverbox").attr("height",height).attr("width",width).attr("x",x).attr("y",y).style("stroke","yellow").style("stroke-width","2px").attr("fill","none");
        }    
    },
    generateImage : function(svg1,svg2){
       var image1 = new Image();
       var image2 = new Image();
       let svge1 = new XMLSerializer().serializeToString(document.querySelector("#"+svg1).querySelector("#svg"));
       let svge2 = new XMLSerializer().serializeToString(document.querySelector("#"+svg2).querySelector("#svg"));
 
//       let imageholder = document.createElement('div');
//       imageholder.id = "giimage";
//       document.body.appendChild(imageholder);      
//       document.getElementById('giimage').appendChild(image);
       var canvas = document.createElement('canvas');
       canvas.id = "fimage"
       canvas.width = 3500;
       canvas.height = 3400;       
       image1.onload = function(){ 
         var context =  canvas.getContext('2d');
         context.webkitImageSmoothingEnabled = true;
         context.mozImageSmoothingEnabled = true;
         context.imageSmoothingEnabled = true;
         context.drawImage(image1, 0, 0, 3500,1400);
      }
      image1.src = 'data:image/svg+xml,' + escape(svge1);  
      
      image2.onload = function(){ 
         var context =  canvas.getContext('2d');
         context.webkitImageSmoothingEnabled = true;
         context.mozImageSmoothingEnabled = true;
         context.imageSmoothingEnabled = true;
         context.drawImage(image2, 0, 1800, 3500,1400);
         document.body.appendChild(canvas);  
         var anchor = document.createElement('a');
         anchor. href = canvas.toDataURL('image/png'); // 'image/jpg'
         anchor. download = 'dentalchart.png'; // 'image.jpg'
         anchor. click();         
//         document.getElementById("giimage").remove();   
         document.getElementById("fimage").remove();   
      }
      setTimeout(()=>{
          image2.src = 'data:image/svg+xml,' + escape(svge2);  
      },1000);
    },
    escapeUnicode: function(str){
       return str.replace(/[^\0-~]/g, function(ch) {
           return "\\u" + ("000" + ch.charCodeAt().toString(16)).slice(-4);
       });        
    }  
  }
  </script>   
