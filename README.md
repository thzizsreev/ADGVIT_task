# ADGVIT_task
task of ADGVIT
BLOCK CHAIN task

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleStorage {
    struct Todo{
        string task;
        bool state;
    }
  Todo[] public todos;
  function create(string calldata _text) public {
    
    Todo memory watch;
    watch.task = _text;
    todos.push(watch);
  }
  function get(uint id) public view returns (string memory task,bool state){
    Todo storage todo = todos[id];
    return (todo.task,todo.state);
  }

  function taskToggle(uint id) public {
    Todo storage temp;
    temp = todos[id];
   temp.state = !temp.state;
  }

  function updateTask(uint id, string calldata _text) public{
         todos[id].task = _text;
         
  }

  function deleteTask(uint id) public {
    require(id < todos.length, "index outta bounds");

     for(uint i = id; i< todos.length-1;i++){
        todos[i] = todos[i+1];
     }
     todos.pop();
  }
}
