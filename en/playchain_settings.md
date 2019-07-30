# Manage PlayChain Settings

There are two types of settings in PlayChain:

_chain_parameters_ and _playchain_parameters_

`curl -X POST playchain.prod.totalpoker.io:8500 -d '{"jsonrpc":"2.0","method":"call","params":[0, "get_global_properties",[]],"id":0}'|python3 -m json.tool`

— to see _chain_parameters_

`curl -X POST playchain.prod.totalpoker.io:8500 -d '{"jsonrpc":"2.0","method":"call","params":["playchain", "get_playchain_properties",[]],"id":0}'|python3 -m json.tool`

— to see _playchain_parameters_

The first group is fully consistent with the BitShares chain_parameters (that is PlayChain core in the sense of blockchain implementation) and managed by core committee. This committee is managed through operations:

_committee_member_create_operation_  
_committee_member_update_operation_

Parameters (that include, for instance, amount of fee for transactions) are changed using oparation:

_committee_member_update_global_parameters_operation_

and proposals technique. Operations:

_proposal_create_operation_  
_proposal_update_operation_  
_proposal_delete_operation_

In details see:    
* [What is the BitShares committee](https://how.bitshares.works/en/master/bts_holders/community_members.html)
* [How BitShares proposals technique works on the example of proposed transactions](https://how.bitshares.works/en/master/user_guide/fund_account.html)

The second group (_playchain_parameters_) are managed by special PlayChain committee.
Elections to a special committee are carried out by analogy with the BitShares committee, except that only the owner of the room, who is the game witness, can be a member of this committee.

Parameters (that include, for instance, referral network coefficients) are changed using oparation:

_playchain_committee_member_update_parameters_operation_  
_playchain_committee_member_update_parameters_v2_operation_

PlayChain committee is managed using oparation:

_playchain_committee_member_create_operation_  
_playchain_committee_member_update_operation_ 

To perform PlayChain-specific operations (playchain_ *) now customer can use the console wallet (included in [playchain-core](https://github.com/totalgames/playchain-core.git)) or write your own application using the C ++ library [playchain-client](https://github.com/totalgames/playchain-client.git).
