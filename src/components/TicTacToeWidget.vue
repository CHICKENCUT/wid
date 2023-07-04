<template>
    <div>
      <h2>Tic Tac Toe Game</h2>
      <div class="board">
        <div
          v-for="(cell, index) in board"
          :key="index"
          class="cell"
          @click="makeMove(index)"
        >
          <span v-if="cell">{{ cell }}</span>
        </div>
      </div>
      <button @click="resetBoard">Ulangi Permainan</button>
      <p>{{ status }}</p>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        board: Array(9).fill(''),
        currentPlayer: 'X',
        gameOver: false,
      };
    },
    computed: {
      status() {
        return `Player ${this.currentPlayer}'s turn`;
      }
    },
    methods: {
      makeMove(index) {
        if (!this.board[index] && !this.gameOver) {
          this.board.splice(index, 1, this.currentPlayer);
          this.currentPlayer = this.currentPlayer === 'X' ? 'O' : 'X';
          this.checkWinner();
        }
      },
      checkWinner() {
        const winningCombos = [
          [0, 1, 2],
          [3, 4, 5],
          [6, 7, 8],
          [0, 3, 6],
          [1, 4, 7],
          [2, 5, 8],
          [0, 4, 8],
          [2, 4, 6],
        ];
  
        for (let combo of winningCombos) {
          const [a, b, c] = combo;
          if (
            this.board[a] &&
            this.board[a] === this.board[b] &&
            this.board[a] === this.board[c]
          ) {
            this.gameOver = true;
            alert(`Player ${this.board[a]} wins!`);
            return;
          }
        }
  
        if (this.board.every(cell => cell)) {
          this.gameOver = true;
          alert("It's a tie!");
        }
      },
      resetBoard() {
        this.board = Array(9).fill('');
        this.currentPlayer = 'X';
        this.gameOver = false;
      },
    },
  };
  </script>
  
  <style scoped>
  .board {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 10px;
  }
  
  .cell {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100px;
  height: 100px;
  border-radius: 50%;
  border: 1px solid #ccc;
  cursor: pointer;
  font-size: 24px;
  background-color: #f2f2f2;
  transition: background-color 0.3s ease;
}

  
  .cell:hover {
    background-color: #e0e0e0;
  }
  
  button {
    margin-top: 10px;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    background-color: #2196f3;
    color: #fff;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  button:hover {
    background-color: #1976d2;
  }
  
  button:active {
    background-color: #1565c0;
  }
  
  button:focus {
    outline: none;
  }
  </style>
  
