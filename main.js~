

function init() {

    var width  = 640;
    var height = 640;
    var canvas = document.getElementById( "myCanvas" );
    var ctx    = canvas.getContext( "2d", { } );

    drawArchimedeanSpiral( ctx, 0, 0, width, height );
}

function drawArchimedeanSpiral( ctx, x, y, width, height ) {

    var center    =  { x : x + width/2.0,
		       y : y + height/2.0
		     };
    var stepCount = 512;
    var DELTA     = 65.0;
    var ROTATIONS = 4.5;

    var Color     = function(r,g,b) {
	this.r = r;
	this.g = g;
	this.b = b;
	this.toString = function() { return "rgb(" + this.r + "," + this.g + "," + this.b +")"; };
	this.scaleTo  = function(color,t) {
	    return new Color( Math.floor(this.r + (color.r-this.r)*t),
			      Math.floor(this.g + (color.g-this.g)*t),
			      Math.floor(this.b + (color.b-this.b)*t)
			    );
	};
    };

    ctx.lineWidth   = 2;
    var startColor = new Color(256,0,0);
    var endColor   = new Color(0,64,128);
    ctx.strokeStyle = startColor.toString(); //'green';
    
    

    var theta    = 0.0;
    var delta    = 0.0;  // pixel per round
    var oldPoint = { x: center.x, y : center.y };
    var point, t;
    for( var step = 0; step < stepCount; step++ ) {
	t       = step/(stepCount-1);
	console.debug( "t=" + t + ", color=" + startColor.scaleTo(endColor,t).toString() );
	point = { x : center.x + Math.cos(theta)*delta,
		  y : center.y + Math.sin(theta)*delta };
	ctx.strokeStyle = startColor.scaleTo(endColor,t).toString();
	ctx.beginPath();
	ctx.moveTo( oldPoint.x, oldPoint.y );
	ctx.lineTo( point.x, point.y );
	ctx.stroke();
	theta -= ROTATIONS*(Math.PI*2)/stepCount;
	delta += DELTA/(stepCount/ROTATIONS);
	oldPoint.x = point.x;
	oldPoint.y = point.y;
    }     
}
