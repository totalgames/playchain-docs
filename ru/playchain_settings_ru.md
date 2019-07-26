# Управление настройками PlayСhain

В PlayChain есть два типа настраиваемых параметров:

_chain_parameters_ и _playchain_parameters_

`curl -X POST playchain.prod.totalpoker.io:8500 -d '{"jsonrpc":"2.0","method":"call","params":[0, "get_global_properties",[]],"id":0}'|python3 -m json.tool`

чтобы посмотреть _chain_parameters_

`curl -X POST playchain.prod.totalpoker.io:8500 -d '{"jsonrpc":"2.0","method":"call","params":["playchain", "get_playchain_properties",[]],"id":0}'|python3 -m json.tool`

чтобы посмотреть _playchain_parameters_

Первая группа полностью соответствует BitShares chain_parameters (который является ядром PlayChain реализующим блокчейн составляющую)
и управляется комитетом ядра. Этот комитет формируется при помощи операций:

_committee_member_create_operation_
_committee_member_update_operation_

Свойства (в которые входит например размер комиссий за операции) изменяются посредством операции:

_committee_member_update_global_parameters_operation_

и механизма proposals. Операции:

_proposal_create_operation_
_proposal_update_operation_
_proposal_delete_operation_
   
Подробнее СМ:    
* [что такое комитет BitShares](https://how.bitshares.works/en/master/bts_holders/community_members.html)
* [как работает механизм proposals BitShares на примере Proposed Transactions](https://how.bitshares.works/en/master/user_guide/fund_account.html)
     
Вторая группа (_playchain_parameters_) управляется специальным комитетом.
Выборы в специальный комитет осуществляются по аналогии с BitShares комитетом за исключением того, что членом этого комитета может быть только владелец комнаты, он же игровой свидетель (game witness)

Свойства (в которые входит например коэффициенты реферальной системы) изменяются посредством операций:

_playchain_committee_member_update_parameters_operation_
_playchain_committee_member_update_parameters_v2_operation_

Игровой комитет управляется при помощи операций:

_playchain_committee_member_create_operation_
_playchain_committee_member_update_operation_

Выполнять специфические для PlayChain операции (playchain_*) сейчас можно из консольного кошелька cli_wallet (входит в https://github.com/totalgames/playchain-core.git) или при помощи С++ библиотеки  https://github.com/totalgames/playchain-client.git.

