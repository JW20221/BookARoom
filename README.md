# BookARoom

## Group members 

- Rattazzi, Giacomo
- Do Vale Anes, Daniel 
- Wang, Jingmin 
- Farhat, Ahmed 

## Project Description 
The “BookARoom” is a hotel reservation website where users can book a room. The website is owned by a single hotel. The hotel has different types of rooms, and each type has a specific number of beds and other services. Anyone can become a client and make a reservation, but for that he needs to make an account and log in.

## Model
### User
A user is defined by the following data :
- a first name,
- a last name,
- a password,
- a unique email address,
- a phone number,
- a method of payment (credit card):
    - 16-digits number, 
    - Expiration date,
    - 3-digits number verification code.
- a booking in which we keep the room the user wants to reserve.

Users can perform the following actions :
- complete their booking,
- change the room reservation,
- change the method of payment,
- verify the reservation (date and type of room), 
- verify their password when logging in.

### Booking

a user’s **Booking** is implemented as a separate object defined by the following data : 
- a list of the room(s) the user wants to book,
- a list of the room(s) the user has booked,
- all the information about the reservation (cost, dates of availability, number of people, room number). 

Users can perform the following actions on their booking bags : 
1. add a room reservation to their booking, 
2. change the dates of reservation,
3. change the type of room,  
4. remove a room reservation to their booking,
5. empty their booking cart after completing their booking.

### Room 

A **room** is defined by the following data:
- a unique number,
- the type of room, 
- a price,
- the number of guests that can sleep in the room,

### Preferences/Recommendation

User’s **Preferences/Recommendation** is implemented as a separate object defined by the following data: 

- the type of food prefered,
- price range,
- distance from the hotel,


Users can perform the following actions on the preferences/recommendation page:
1. Add preferences
2. Remove preferences
3. Search for restaurants that fit the user’s preferences

### Restaurant

A **restaurant** is defined by the following data:
- a unique restaurant name,
- the type of food, 
- the price range,
- the opening hours,
- the distance from the hotel. 


## View

The first version of our Hotel Reservation Project will be a text User Interface (UI), and the second version will switch to a simple web UI.

When launched, the application starts by printing the following menu, called **Main Page**, and waits for the user to choose an option:
	
	Enter:
	[q] to quit the application
	[1] to login
	[2] to create a user account
	[3] to browse rooms


- **[q] to quit the application.** If the user types [q], the application stops.
- **[1] to login.** If the user types [1], the application asks the user to type their username and password, respectively. If the username and password are correct, the User Home Page is displayed. 
- **[2] to create a user account.** If the user types [2], the application asks the user to type a username, a first name, a last name, a phone number, an email, a password, and a method of payment (credit card defined by: a 16-digits number, an expiration date, and a 3-digits number verification code). 
- **[3] to browse rooms.** If the user types [3]. a list of rooms will be printed. 

**Anything else.** If the user types anything other than [q], [1], [2], and [3], a warning message is printed. 

After login [1], the application prints the following menu, called **User Home Page**, and waits for the user to choose an option:

	Enter:
	[q] to log out
	[1] to browse and book new rooms
	[2] to show booked rooms
	[3] to get restaurant recommendations
  	[4] to show user information

- **[q] to log out.** If the user types [q], the user logs out and goes back to the Main Page. 
- **[1] to book a new room.** If the user types [1], the **Booking Page** is displayed. 
- **[2] to show booked rooms.** If the user types [2], the application prints the user's previous reservation information.
- **[3] To get restaurant recommendations.** If the user types [2], the application prints all possible preferences, prints the following menu, and waits for the user to choose an option: 

    	Enter:
    	[q] to go back
    	[1] to add a preference
    	[2] to get recommendations
  

- **[q] to go back.** If the user types [q], the application goes back to the User Home Page. 
- **[1] to add a preference.** If the user types [1], the user is asked to type a preference. 
- **[2] To get recommendations.** If the user types [2], a list of the best restaurants according to the user’s preferences is printed. 

Finally the last option of the **User Home Page:** 

- **[3] to show user information.** If the user types [3], the application prints the user’s information.

In the **Booking Page**, the application will ask the user to choose check-in and check-out dates and the number of guests. The user enters the dates and guest number. If  there are rooms that meet the requirements, a list of rooms is printed, otherwise, “No room available.” will be printed. When there are rooms available, users will be asked to choose a room. Once a room is chosen, the **Confirmation Page** is displayed. 

In the **Confirmation Page**, the user is asked to confirm his reservation. If the credit card is valid, the reservation is added to the user booked rooms page, and a “Thank you for your reservation.” message is printed. 



## Controller

- **LoginController:** This controller holds username and password information of a user who wants to log in. If the user successfully logs in, the controller holds the currentUser. In addition, it manages login and log out functions of the application. 

- **UserController:** This controller holds first name, last name, email, password, phone number, reservation number, and amount information. It also manages creation of a new user account, adding a payment method, and completing the booking.

- **RoomController:** This controller holds room number information; it manages adding a reservation to a shopping cart and removing a reservation from the shopping cart. 

- **PreferencesController:** This controller holds the user’s preferences; it manages adding a preference and removing a preference from the user’s preferences list.


## Mock Database

The mock database class will manage adding, changing and removing User, Room and  Restaurants objects. 

## Exceptions							

- **AlreadyExistsException:** When a user wants to create a new account, this exception must be thrown if the email is already used by another user. 

- **DoesNotExistsException:** When a user wants to log in (and the username does not exist), to create a new account (and the username is not in-use), to add a room number to their cart (and the room is not in the hotel's room list), and to remove a room from their booking (and the room is not in the booking), this exception must be thrown. 

- **InvalidCreditCardException:** When a user wants to confirm a room reservation, the user should have a valid card number. A valid credit card requires a 16-digits number, an expiration date which should be at a further date than the current date, and a 3-digits number verification code. If not, this exception must be thrown. 

- **AlreadyBookedException:** When a user wants to confirm a room reservation, the room should be available at the chosen date. If not, this exception must be thrown.

- **NothingFoundException:** When a user asks for restaurant recommendation, his preferences should match at least one restaurant. If not, this exception must be thrown.  

## Final Remarks

Other features may be added later and some may be changed. We can add a new page for the employees. The employee can verify and add new rooms and confirm reservations. Another idea would be to add reviews for the rooms. Each room would have different ratings, and the user could give his own rating and add a comment. 
