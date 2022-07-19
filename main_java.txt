package java_20;

import java.awt.DisplayMode;
import java.security.PublicKey;
import java.util.ArrayList;
import java.util.Iterator;
import java.util.LinkedList;
import java.util.ListIterator;
import java.util.Scanner;

import javax.sql.rowset.CachedRowSet;

public class Main_clss {
	private static ArrayList<Album> albums =new ArrayList<>();

	public static void main(String[] args) {
		Album album= new Album("Album 1","dc/me");
		
		album.addSong("life", 4.5);
		album.addSong("go car", 1.5);
		
		album.addSong("Memory", 3.5);
		
		album.addSong("life", 4.5);
		album.addSong("life", 4.5);
		albums.add(album);
		
		
		album= new Album("Album 2","taylor");
		
		album.addSong("blank space", 4.5);
		album.addSong("u belong", 1.5);
		
		album.addSong("firework", 3.5);
		albums.add(album);
		
	LinkedList<Song>playlist_1=new LinkedList<>();

	albums.get(0).addToPlaylist("life", playlist_1);
	albums.get(0).addToPlaylist("go car", playlist_1);
	albums.get(1).addToPlaylist("blank space", playlist_1);
	albums.get(1).addToPlaylist("u belong", playlist_1);
		
	
	play(playlist_1);

	}
	private static  void play(LinkedList<Song>playList) {
		Scanner sc =new Scanner(System.in);
		boolean quit=false;
		boolean forward=true;
		ListIterator<Song>listLterator= playList.listIterator();
		
		if(playList.size()==0)
		{
			System.out.println("the list has no song");
			PrintMenu();
		}
		while(!quit) {
			int action=sc.nextInt();
			sc.nextLine();
			switch(action) {
			
			case 0:
				System.out.println("no song to play\n");
				quit=true;
				break;
			case 1:
				  if(!forward)
				  {
					 if(listLterator.hasNext()) {
						 listLterator.next();
						 
					 }
					 forward =true;
					 if(listLterator.hasNext()) {
						 System.out.println("Now playing"+listLterator.next().toString());
					 }
					 else {
						 System.out.println("reached the end of the list no songes to play");
						 forward=false;
					 }
					 break;
				  }
			case 2: if(forward) {
				if(listLterator.hasPrevious()) {
					listLterator.previous();
					
				}
				forward=false;
			}
			if(listLterator.hasPrevious()) {
				System.out.println("now playong song is"+listLterator.previous().toString());
				
			}else {
				System.out.println("this is the first song");
				forward=false;
			}
				break;
				
			case 3: if(forward) {
				if(listLterator.hasPrevious()) {
					System.out.println("now playong song is"+listLterator.previous().toString());
					forward=false;
				
			}else {
				System.out.println("this is the first song");
			}
				
			
			}else {
				if(listLterator.hasNext()) {
				 System.out.println("Now playing"+listLterator.next().toString());
				 forward=true;
				
			}else{
				 System.out.print("your have reache end of list");
			   }
				
			}
			break;
			case 4:
				printPlayList(playList);
				break;
				
			case 5:
				PrintMenu();
				break;
				
			case 6:
			       if(playList.size()>0) {
			    	   listLterator.remove();
			    	   if(listLterator.hasNext())
			    	   {
			    		   System.out.println("Now playing"+listLterator.next().toString());
							 
			    	   }
			    	   else {
			    		   if(listLterator.hasPrevious())
			    			   System.out.println("now playong song is"+listLterator.previous().toString());
			    	   }
			    	   
			    	   
				
			
		}
	}}
}
	 private static void PrintMenu() {
		 System.out.println("The avalable options are\n");
		 System.out.println("1.to play next song\n"+
				 			"2.paly previous song\n"+"3.replay the song\n"
				 +"4.list all songs\n"+"5.delete the current song\n"+"0.to quit\n");
		 
		
	}
              private static void  printPlayList(LinkedList<Song>playList) {
            	  Iterator<Song>iterator=playList.iterator();
            	  System.out.println("------------------------");
            	  
            	  while(iterator.hasNext())
            	  {
            	     System.out.println(iterator.next());
				
              }
            	  System.out.println("_________________________");
}
}