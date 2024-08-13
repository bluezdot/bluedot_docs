API: https://testnet.toncenter.com/api/v3/index.html#/blockchain/api_v3_get_adjacent_transactions
```json
{
  "transactions": [
    {
      "account": "0:5B6A643CF4E32FF0391C476456FED5BDB17EF10A55CBB7C2980C76D4AAD07875",
      "hash": "Jv81SPUJbodVgsHB+lo0/jEJDaidYQYivJDg+rz+ITA=",
      "lt": "24264044000001",
      "now": 1722422624,
      "mc_block_seqno": 21586062, // ?
      "trace_id": "Jv81SPUJbodVgsHB+lo0/jEJDaidYQYivJDg+rz+ITA=",
      "prev_trans_hash": "kUMJfVqMbssHL8zSMF1RSChkCh2DiEiDUDnj7+gbK08=",
      "prev_trans_lt": "24263927000001",
      "orig_status": "active",
      "end_status": "active",
      "total_fees": "2123803",
      "description": {
        "type": "ord",
        "aborted": false,
        "destroyed": false,
        "credit_first": true,
        "storage_ph": {
          "storage_fees_collected": "72",
          "status_change": "unchanged"
        },
        "compute_ph": {
          "skipped": false,
          "success": true,
          "msg_state_used": false,
          "account_activated": false,
          "gas_fees": "1323200",
          "gas_used": "3308",
          "gas_limit": "0",
          "gas_credit": "10000",
          "mode": 0,
          "exit_code": 0,
          "vm_steps": 68,
          "vm_init_state_hash": "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA=",
          "vm_final_state_hash": "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA="
        },
        "action": {
          "success": true,
          "valid": true,
          "no_funds": false,
          "status_change": "unchanged",
          "total_fwd_fees": "400000",
          "total_action_fees": "133331",
          "result_code": 0,
          "tot_actions": 1,
          "spec_actions": 0,
          "skipped_actions": 0,
          "msgs_created": 1,
          "action_list_hash": "zwHeYeqotxzkEMtaxyDK69k7urLdK1jP5VsAHuPlkfc=",
          "tot_msg_size": {
            "cells": "1",
            "bits": "857"
          }
        }
      },
      "block_ref": {
        "workchain": 0,
        "shard": "6000000000000000",
        "seqno": 23167862
      },
      "in_msg": {
        "hash": "RhrVTJxVy89oSoONtxcjAemKpyWyYva5L7XmXPPdn20=",
        "source": null,
        "destination": "0:5B6A643CF4E32FF0391C476456FED5BDB17EF10A55CBB7C2980C76D4AAD07875",
        "value": null,
        "fwd_fee": null,
        "ihr_fee": null,
        "created_lt": null,
        "created_at": null,
        "opcode": "0x9c7b4878",
        "ihr_disabled": null,
        "bounce": null,
        "bounced": null,
        "import_fee": "0",
        "message_content": {
          "hash": "wgyD6chLMrhiRBVE8eQEuajFrLkvGHQXWme7SexHjd4=",
          "body": "te6cckEBAgEAmgABnJx7SHhTR/PSlEK/KmjzfXKJfsrqYfm/dIgHcqGbpgmQ3QryxKgBFqJDh0Sdao9tq8pkFn4EinA1HK0KtHLUKgcpqaMXZqoVlgAAABcAAQEAjkIAQauz11y04cIsOWoxn93X75B8l752j9cHvMAlYE+ZlQygDk4cAAAAAAAAAAAAAAAAAAAAAAAAWWVzc3NzcyBJbSBkb25lqdKygA==",
          "decoded": null
        },
        "init_state": null
      },
      "out_msgs": [
        {
          "hash": "UOCirTmzfXVxvp2+H6lyCTJZjXTMNNLGye+c/w2TskQ=",
          "source": "0:5B6A643CF4E32FF0391C476456FED5BDB17EF10A55CBB7C2980C76D4AAD07875",
          "destination": "0:835767AEB969C3845872D4633FBBAFDF20F92F7CED1FAE0F79804AC09F332A19",
          "value": "30000000",
          "fwd_fee": "266669",
          "ihr_fee": "0",
          "created_lt": "24264044000002",
          "created_at": "1722422624",
          "opcode": "0x00000000",
          "ihr_disabled": true, // ?
          "bounce": false,
          "bounced": false,
          "import_fee": null,
          "message_content": {
            "hash": "aRDz1FI1M1N8oA1vtR6SRNPsIM6x3hR93WwNCtruwrM=",
            "body": "te6cckEBAQEAFQAAJgAAAABZZXNzc3NzIEltIGRvbmV4d0SJ",
            "decoded": {
              "type": "text_comment",
              "comment": "Yesssss Im done"
            }
          },
          "init_state": null
        }
      ],
      "account_state_before": { // state of caller, can check for frozen state
        "hash": "odGfzo/QLhouwe/TasiiTeGxeU1LZXhhmt4tshUSLmY=",
        "balance": "17301017743",
        "account_status": "active",
        "frozen_hash": null,
        "data_hash": "jTGxXTz8bcxkMrISrMkG0bsGZGLcg9FoHghpqsXxWyg=",
        "code_hash": "/rX/aCDi/w2Ug+fg1iyBfYRniftK5YDIeIZtlZ2r1cA="
      },
      "account_state_after": {
        "hash": "+kiWay5LvcBwUCI9jx+dQEFVQ69WSTaYQCtFNaJ+na0=",
        "balance": "17268627271",
        "account_status": "active",
        "frozen_hash": null,
        "data_hash": "Kk8iBmXmmB3YJsJB9MJsdCFjHfXnIQeim1BbQztL8WQ=",
        "code_hash": "/rX/aCDi/w2Ug+fg1iyBfYRniftK5YDIeIZtlZ2r1cA="
      }
    }
  ],
  "address_book": { // related address
    "0:5B6A643CF4E32FF0391C476456FED5BDB17EF10A55CBB7C2980C76D4AAD07875": {
      "user_friendly": "0QBbamQ89OMv8DkcR2RW_tW9sX7xClXLt8KYDHbUqtB4dQd_"
    },
    "0:835767AEB969C3845872D4633FBBAFDF20F92F7CED1FAE0F79804AC09F332A19": {
      "user_friendly": "0QCDV2euuWnDhFhy1GM_u6_fIPkvfO0frg95gErAnzMqGea9"
    }
  }
}
```