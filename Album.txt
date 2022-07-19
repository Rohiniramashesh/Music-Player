package java_20;

import java.util.ArrayList;
import java.util.LinkedList;

import javax.lang.model.element.NestingKind;

public class Album {
	//private String name;
	//private String artist;
	private ArrayList<Song>songs;
	
	
	public Album(String name, String artist) {
		
		//this.name = name;
		//this.artist = artist;
		
	}
		
	public Album() {
		
		
	}
	public Song findSong(String title) {
		for(Song checkSong : songs)
		{
				if(checkSong.getTitle().equals(title)) return checkSong;
		}
		return null;
	}
	
	public boolean addSong(String title,double duration)
	{
		if(findSong(title)==null)
		{
			songs.add(new Song(title,duration));
			System.out.println(title+"is successly added to the album");
			return true;
			
		}
		else {
		System.out.println("song already exists in list");
		return false;
	}
	}
	
	public boolean addToPlaylist(int trackNumber,LinkedList<Song> PlayList) {
		int index= trackNumber-1;
		if(index>0 && index<=this.songs.size())
		{
			PlayList.add(this.songs.get(index));
			return true;
		}
		System.out.println("this trackno. does not exist in song list"+trackNumber);
		return false;
	}
	 
	public boolean addToPlaylist(String title,LinkedList<Song>PlayList) {
		for(Song checkSong : this.songs)
		{
			if(checkSong.getTitle().equals(title)) {
				PlayList.add(checkSong);
				return true;
			}
		}
		System.out.println(title+"this song does not exists");
		return false;
		
	}
	
	
		
	
	

}

