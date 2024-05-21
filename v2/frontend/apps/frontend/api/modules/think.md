-   modules
    -   / account
        -   domain
            -   AccountAggregate - what is seen in side bar
            -   AccountDetailsAggregate - what is seen in admin
            -   AccountEvent
        -   queries
            -   getProfile
            -   getDetails -> {balances...}
            -   getActionHistory
            -   getPurchasedLicenses -> Array<{...license, post}>
            -   getBeneficiaryOf // just add to AccountAggregate
            -   getSubscriptions
        -   commands
            -   create
            -   edit
            -   withdraw
            -   deposit
            -   addBeneficiary
            -   removeBeneficiary
            -   cancelClaim
            -   startClaimAsBeneficiary
            -   withdrawAsBeneficiary
    -   / profile
        -   domain
            -   ProfileAggregate -> {profile, verificationStatus, postInteractionSummary}
            -   userPostOptions -> {interactions, areOwnerOf, subscribed, beneficiaryOf}
        -   queries
            -   getProfiles
            -   getProfile
            -   getPosts(filterType, sortType, limit, offset)
            -   getProfileInteractions
            -   getLikedPosts
            -   getPools
        -   commands
            -   subscribe
            -   unsubscribe
            -   sendBonus
    -   / posts
        -   domain
            -   ImagePostAggregate
            -   ArticlePostAggregate
            -   LicenseAggregate
            -   userPostOptions -> {ownedLicenses, interactions, areOwnerOf}
        -   queries
            -   getPosts(filterType, sortType, limit, offset)
            -   getPost -> PostAggregate{post, interactions, profile}
            -   getPostInteractions(account, postId) -> {interactions, licenses}
        -   commands
            -   create
            -   purchaseLicense
            -   interact // make undo-able
    -   / pools
        -   domain
            -   PoolAggregate
            -   PoolPledgerAggregate -> {profile, poolPledger}
            -   PoolEventAggregate -> {poolEvent, pledger, profile}
            -   userPoolOptions -> {events, arePledged, pledged amount, areOwnerOf}
        -   queries
            -   getPools
            -   getPool
            -   getPoolEvents(limit, offset) -> PoolEventAggregate
        -   commands
            -   create
            -   cancel
            -   pledge
            -   unpledge
            -   claim
            -   refund