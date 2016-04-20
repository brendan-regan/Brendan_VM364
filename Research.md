#Research Presentation

The hardest thing for me to figure out so far has been how to use coins to reveal objects in the game. With the help of Wade, we were able to create a single script that connects each coin to each object's relative script. 

	public void MakePathWalkable(string x){

		if (x == "Coin"){
		GameObject.Find("path").GetComponent<PathScript>().MakeTexture("path");
		//path2.GetComponent<PathScript>().MakeTexture();
		}
		if (x == "Coin (1)"){
			GameObject.Find("path (2)").GetComponent<PathScript>().MakeTexture("path (2)");
			//path2.GetComponent<PathScript>().MakeTexture();
		}
		if (x == "Coin (2)") {
			GameObject.Find ("bigtube").GetComponent<Bigtube>().MakeTexture ("bigtube");
		}
	}

	public void MakeTexture(string x){
		if (x == "path") {
			GameObject.Find ("path").GetComponent<PathScript> ().MakePathTexture ();
		}
		if (x == "path (2)") {
			GameObject.Find ("path (2)").GetComponent<PathScript> ().MakePathTexture ();
		}
		if (x == "bigtube") {
			GameObject.Find ("bigtube").GetComponent<Bigtube> ().MakePathTexture ();
		}
	
	
	This way, if a coin is picked up, it calls to a script to make a texture. Take for example line 1, when "coin" is hit, the game system script finds the script for the "path" and looks for the "MakePathTexture" command, which I defined in each object's script. This shows the user the next objective. In order to make the texture, a version of the following must be written in each of the scripts that correspond to each object. 
	
		public void MakePathTexture(){
		this.GetComponent<Renderer>().material.mainTexture = movTexture;
		movTexture.loop = true;
		movTexture.Play();
	}	

I found out most of this information through help from Wade and Sasha... The Unity forums helped a lot as well, since I didn't know how to make the textures animate or loop. 

[Unity Forum](http://docs.unity3d.com/Manual/class-MovieTexture.html) - While some of this info was useful, not all of it worked, and it required a lot of trial and error..

This is made by a command called "Movie Texture" which prompts a box in Unity where you can add your .mov file. I defined this in my script, and in order to make the video loop, I needed to add the script "movTexture.loop = true" and "movTexture.Play();". There used to be a "Loop" setting on the inspector window, but they have made that obsolete in the new version of Unity.

It seems so simple now that I know how to do it, but since I had no prior experience with scripting before, this all was a tall order..
