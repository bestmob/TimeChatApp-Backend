= TimeChat APIs

= iOS TimeChat App back-end service


== API

=== Accounts endpoint

==== Check sigined user
    
    POST: /accounts/check_token

    parameters:
        token           String *required

==== Signup

    POST: /accounts/sign_up

    parameters:
        email               String *required
        password            String *required
        user_id             String *required
        user_name           String *required
        dev_id              String *required
        social_type         String *required
        remote_avatar_url   String *required
        time_zone           String *required


==== Signin

    POST: /accounts/sign_in

    parameters:
        email              String *required
        password           String *required
        dev_id             String *required
        time_zone           String *required

==== Forgot Password

    POST: /accounts/forgot_password

    parameters:
        email              String *required

==== Change Profile

    POST: /accounts/change_profile

    parameters:
        old_password		String *required
        new_password		String *required
        user_name 			String *required
        new_email			String *required
        avatar 				File
        token 				String *required

==== Push Setup
    
    POST: /accounts/push_setting
    
    parameters:
        token             String *required
        push_enable       String 
        sound_enable      String

==== Sound Setup
    
    POST: /accounts/sound_setting
    
    parameters:
    	push_sound		  String *required
        token             String *required

==== Privacy Setup

    POST: /accounts/privacy_setting

    parameters:
        token                 String *required
        auto_accept_friend    Boolean 
        auto_notify_friend    Boolean

==== Theme Setup

    POST: /accounts/theme_setting

    parameters:
        token                 String *required
        theme_type			  Int

==== Set Online

    POST: /accounts/set_online

    parameters:
        token                 String *required

==== Set Offline

    POST: /accounts/set_offline

    parameters:
        token                 String *required

==== Get Setting

    GET: /accounts/setting

    parameters:
        token                 String *required


=== Friends endpoint

==== Get Friend List

    GET: /friends

    parameters:
        token       String *required

==== Get Facebook Users

    GET: /friends/facebook_users

    parameters:
        token       String *required

==== Get Google Users

    GET: /friends/google_users

    parameters:
        token       String *required

==== Get Phonebook Users

    GET: /friends/phonebook_users

    parameters:
        token       String *required
        emails      String *required 

==== Get Search Friend

    GET: /friends/search_friend

    parameters:
        token               String *required
        email               String *required

==== Add Friend

    POST: /friends/add_friend

    parameters:
        token               String *required
        email               String *required	

==== Add Friend By User Name

    POST: /friends/add_friend_by_username

    parameters:
        token               String *required
       	username            String *required

==== Add Friends

    POST: /friends/add_friends

    parameters:
        token               String *required
        user_ids            String *required

==== Add Friend By Phone Book

    POST: /friends/add_friends_by_phone_book

    parameters:
        token               String *required
       	emails            	String *required(delimiter ',')

==== Accept Friend

    POST: /friends/accept_friend

    parameters:
        token               String *required
        friend_id           String *required
        notification_id		String *required

==== Decline Friend

    POST: /friends/decline_friend

    parameters:
        token               String *required
        friend_id           String *required
        notification_id		String *required

==== Ignore Friend

    POST: /friends/ignore_friend

    parameters:
        token               String *required
        friend_id           String *required

==== Remove Ignore Friend

    POST: /friends/remove_ignore_friend

    parameters:
        token               String *required
        friend_id           String *required

==== Remove Friend
    
    POST: /friends/remove_friend
    
    parameters:
        token               String *required
        friend_id           String *required

==== Favorite Friend
    
    POST: /friends/favorite_friend
    
    parameters:
        token               String *required
        friend_id           String *required

==== Remove Favorite Friend
    
    POST: /friends/remove_favorite_friend
    
    parameters:
        token               String *required
        friend_id           String *required


=== Notification Endpoints

==== Get Notifications

    GET: /notifications

    parameters:
        token               String *required

==== Get Notification Count

    GET: /notifications/notification_count

    parameters:
        token               String *required

==== Delete notification

    POST: /notifications/delete

    parameters:
        token               String *required
        notification_id     String *required

==== Had Read notifications

    POST: /notifications/had_read_notification

    parameters:  
        token               String *required
        notification_id     String *required

==== Remove All notification

    POST: /notifications/remove_all

    parameters:
        token               String *required


=== Medias Endpoints

==== Get all media

    GET: /medias

    parameters:
        token               String *required

==== Get medias for friend

    GET: /medias/medias_for_friend

    parameters:
        token               String *required
        friend_id           String *required

==== Get all shared media

    GET: /medias/shared_media

    parameters:
        token               String *required

==== Get media info by media id

    GET: /medias/media_info

    parameters:
        token               String *required
        media_id            String *required

==== Upload new media

    POST: /medias/upload

    parameters:
        token               String *required
        media               Image Data
        media_type          String *required [photo, video]

        EX:
        curl -F "token=gtr-YzGepAiTJv8yCed1" -F "media=@/Volumes/Work/Images/avatar.png" /medias/upload

==== Update media

    POST: /medias/update

    parameters:
        token               String *required
        media_id            String *required
        media               Image Data

==== Share media

    POST: /medias/share

    parameters:
        token               String *required
        media_id            String *required
        friend_id           String *required

==== Share medias

    POST: /medias/share_medias

    parameters:
        token               String *required
        type                Integer
        media_id            String *required
        friend_ids          String *required


=== Comments Endpoints

==== Get comments by media id

    GET: /comments

    parameters:
        token       String *required
        media_id    String *required

==== Add comment

    POST: /comments/add_comment

    parameters:
        token       String *required
        media_id    String *required
        comment     String *required
