UpdateAuctionRecord
===================

import java.util.Date;

public class UpdateAuctionFile
{

    //Desc: adds a new auction record file to the text file
    //Pre: the AuctionPaintings.dat file must exist
    //Post: A new auction record is created
    public static void addAuctionFile()	
    {
        try
        {
            boolean	      done = false;		        // terminates while-loop
            char	      choice;	                        // user's choice
            AuctionPainting m = new AuctionPainting(); 

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
                        m.setArtistLastName(lname);
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
    
    //Desc: updates the AuctionPaintings file by searching for the last name of the artist
    //      and painting title
    //Pre: the AuctionPaintings.dat file must exist
    //Post: The AuctionPaintings file is updated
    public static void updateAuctionPainting()
    {

    try
    {
	boolean	      done = false;		        // terminates while-loop
	boolean	      found = false;		        // tells if investment is found
	char	      c;			        // character entered by user
	String        title;                            // buffer for line of characters
        String        lName;
	char	      choice;	                        // user's choice
        AuctionPainting    a = new AuctionPainting();    // investment to be modified

	while (!found && !done)
	{
            System.out.println ("Please enter the following for the auction painting you want to update "
                    + "\t   Last name of Artist then press <ENTER> "
                    + "and Painting Title then press <ENTER>"); 

            lName = UserInterface.getString();
            title = UserInterface.getString();

	    found = a.find (lName,title);

	    if (!found)
	    {
		System.out.println ("Painting by " + lName +" Titled "+ title + " was not found.");
		System.out.println ("Would you like to enter another Artist Name and Title?");

		choice = UserInterface.getChar();

		if (choice == 'n')
		{
		  done = true;
		}
            }
	}

	if (!found)
	{
	    return;
	}

	while (!done)
	{
		while (!done)
		{
                    UserInterface.clearScreen ();

                    System.out.println ("\t           UPDATE AUCTION PAINTING\n\n"); //this needs to change based on what updates we allow
                    System.out.println ("\t Oglesby Art Pricing System\n\n");
                    System.out.println ("\t        1. Update Artist first name\n");
                    System.out.println ("\t        2. Update Artist last name\n");
                    System.out.println ("\t        3. Update Title of Work\n");
                    System.out.println ("\t        4. Update Date of Work\n");
                    System.out.println ("\t        5. Update Medium\n");
                    System.out.println ("\t        6. Update Date of Auction\n");
                    System.out.println ("\t        7. Update Auction Sales Price\n");
                    System.out.println ("\t        8. Exit to menu\n\n");
                    System.out.println ("Enter your choice and press <ENTER>: ");

                    try
                    {
			choice = UserInterface.getChar();

			switch (choice)
			{
                            case '1':
                                a.updateArtistsFirstName();
                                break;

                            case '2':
                                a.updateArtistsLastName();
                                break;
                            
                            case '3':
                              a.updateTitleOfWork();
                              break;

                            case '4':
                                a.updateDateOfWork();
                                break;
                            case '5':
                                a.updateMedium();
                                break;
                            case '6':
                                a.updateDateofAuction();
                                break;
                            case '7':
                                a.updateAuctionSalesPrice();
                                break;
                            case '\n':
                              done = true;
				  break;

                            default:
                              System.out.println ("\n\nNot a valid choice\n");
                              UserInterface.pressEnter();
                              break;
			}
                     }
			catch (Exception e)
			{
			    System.out.println ("***** Error: UpdateAuctionFile.updateAuctionPainting() *****");
			    System.out.println ("\t" + e);
			}

			if (!done)
			{
		            a.print ();
		            UserInterface.pressEnter();
			}
                }
        }

	a.save ();
    }
    catch (Exception e)
    {
	    System.out.println ("***** Error: UpdateAuctionFile.updateAuctionPainting() () *****");
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

