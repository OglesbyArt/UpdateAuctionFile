UpdateAuctionRecord
===================

import java.util.Date;

public class UpdateAuctionRecord 
{

    //Desc: adds a new auction record file to the text file
    //Pre: the AuctionPaintings.dat file must exist
    //Post: A new auction record is created
    public static void addArtistFile()	
    {
        try
        {
            boolean	      done = false;		        // terminates while-loop
            char	      choice;	                        // user's choice
            MasterpieceAuctionPainting m = new MasterpieceAuctionPainting(); 

		while (!done)
		{
			UserInterface.clearScreen ();

			System.out.println ("\t           ADD NEW AUCTION RECORD TO FILE\n\n");
			System.out.println ("\t             Oglesby Art Pricing System\n\n");

                        System.out.println ("\t        Enter Artists First Name: ");
                        String fname = UserInterface.getString();
                        m.setArtistFirstName(fname);
			System.out.println ("\t        Enter Artists Last Name: ");
                        String lname = UserInterface.getString();
                        m.setArtistsLastName(lname);
			System.out.println ("\t        Enter Title of Work: ");
                        String title = UserInterface.getString();
                        m.setTitleofWork(title);
                        System.out.println ("\t        Enter Date of Work: ");
                        String temp = UserInterface.getString();
                        Date date = new Date(temp);
                        m.setDateofWork(date);
                        System.out.println ("\t        Enter Date of Auction: ");
                        String t = UserInterface.getString();
                        Date datea = new Date(temp);
                        m.setDateofAuction(datea);
                        System.out.println ("\t        Enter Auction Sales Price: ");
                        double price = UserInterface.getDouble();
                        m.setAuctionSalesPrice(price);

			if (!done)
			{
		            m.print ();
		            UserInterface.pressEnter();
			}
		    }
		

	m.save ();
    }
    catch (Exception e)
    {
	    System.out.println ("***** Error: AssetManager.manageInvestment() () *****");
	    System.out.println ("\t" + e);
    }

  }  

	//Desc: deletes the artist file selected by searching for lastname, 
    //      firstname
    //Pre: the ArtistFile.txt file must exist
    //Post: The Artist file is deleted
    public static void deleteAuctionFile()
    {
        
	System.out.println ("Enter Last Name of Artist and title of painting "
                + "for the file you want to delete you want to delete: ");
	String lname = UserInterface.getString();
        String title = UserInterface.getString();
	//not sure how to do this yet
    }
}
