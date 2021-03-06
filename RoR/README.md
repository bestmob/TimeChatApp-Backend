= TimeChat APIs

= iOS TimeChat App back-end service


== API

=== Accounts endpoint

==== Check sigined user
    
    POST: /api/v1/accounts/check_token

    parameters:
        token           String *required

==== Signup

    POST: /api/v1/accounts/sign_up

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

    POST: /api/v1/accounts/sign_in

    parameters:
        email:              String *required
        password:           String *required
        dev_id:             String *required

==== Change Password

    POST: /api/v1/accounts/change_password

    parameters:
        token             String *required
        old_password      String *required
        new_password      String *required

==== Change User name

    POST: /api/v1/accounts/change_user_name

    parameters:
        token             String *required
        user_name         String *required

==== Change email

    POST: /api/v1/accounts/change_email

    parameters:
        token             String *required
        new_email         String *required

==== Change avatar

    POST: /api/v1/accounts/upload_avatar

    parameters:
        token             String *required
        avatar            Image *required

==== Push setup
    
    POST: /api/v1/accounts/push_setting
    
    parameters:
        token             String *required
        push_enable       String 
        sound_enable      String

==== Get Push Setting
    
    GET: /api/v1/accounts/push_setting
    
    parameters:
        token             String *required

==== Privacy setup

    POST: /api/v1/accounts/privacy_setting

    parameters:
        token                 String *required
        auto_accept_friend    Boolean 
        auto_notify_friend    Boolean

==== Get Privacy Setting

    GET: /api/v1/accounts/privacy_setting

    parameters:
        token             String *required

=== Friends endpoint

==== Get Friend List

    GET: /api/v1/friends

    parameters:
        token       String *required

==== Get Facebook Users

    GET: /api/v1/friends/facebook_users

    parameters:
        token       String *required

==== Get Google Users

    GET: /api/v1/friends/google_users

    parameters:
        token       String *required

==== Get Phonebook Users

    GET: /api/v1/friends/phonebook_users

    parameters:
        token       String *required
        emails      String *required 

==== Get Search Friend

    GET: /api/v1/friends/search_friend

    parameters:
        token               String *required
        email               String *required

==== Add Friend

    POST: /api/v1/friends/add_friend

    parameters:
        token               String *required
        email               String *required

==== Add Friends

    POST: /api/v1/friends/add_friends

    parameters:
        token               String *required
        user_ids            String *required

==== Accept Friend

    POST: /api/v1/friends/accept_friend

    parameters:
        token               String *required
        friend_id           String *required

==== Decline Friend

    POST: /api/v1/friends/decline_friend

    parameters:
        token               String *required
        friend_id           String *required

==== Ignore Friend

    POST: /api/v1/friends/ignore_friend

    parameters:
        token               String *required
        friend_id           String *required

==== Remove Ignore Friend

    POST: /api/v1/friends/remove_ignore_friend

    parameters:
        token               String *required
        friend_id           String *required

==== Remove Friend
    
    POST: /api/v1/friends/remove_friend
    
    parameters:
        token               String *required
        friend_id           String *required


=== Notification Endpoints

==== Delete notification

    POST: /api/v1/notifications/delete

    parameters:
        token               String *required
        notification_id     String *required

==== Had Read notifications

    POST: /api/v1/notifications/had_read_notification

    parameters:  
        token               String *required
        notification_id     String *required


=== Medias Endpoints

==== Get all media

    GET: /api/v1/medias

    parameters:
        token               String *required

==== Get media for period

    GET: /api/v1/medias/media_for_period

    parameters:
        token               String *required
        hour                String *required

==== Get all shared media

    GET: /api/v1/medias/shared_media

    parameters:
        token               String *required

==== Get media info by media id

    GET: /api/v1/medias/media_info

    parameters:
        token               String *required
        media_id            String *required

==== Upload new media

    POST: /api/v1/medias/upload

    parameters:
        token               String *required
        media               Image Data
        media_type          String *required [photo, video]

        EX:
        curl -F "token=gtr-YzGepAiTJv8yCed1" -F "media=@/Volumes/Work/Images/avatar.png" /api/v1/medias/upload

==== Update media

    POST: /api/v1/medias/update

    parameters:
        token               String *required
        media_id            String *required
        media               Image Data

==== Share media

    POST: /api/v1/medias/share

    parameters:
        token               String *required
        media_id            String *required
        friend_id           String *required

==== Share medias

    POST: /api/v1/medias/share_medias

    parameters:
        token               String *required
        type                Integer
        media_id            String *required
        friend_ids          String *required


=== Comments Endpoints

==== Get comments by media id

    GET: /api/v1/comments

    parameters:
        token       String *required
        media_id    String *required

==== Add comment

    POST: /api/v1/comments/add_comment

    parameters:
        token       String *required
        media_id    String *required
        comment     String *required
