<script>
  let data = [
    { id: 1, name: 'foo' },
    { id: 2, name: 'bar' },
    { id: 3, name: 'baz' }
  ];

  const add = () => {
    data = [...data, { id: 4, name: 'qux' }];
  };

  const modify = () => {
    data = data.map(item => {
      if (item.id === 2) {
        return { ...item, name: 'holy' };
      }
      return item;
    });
  };

  const remove = (id) => {
    data = data.filter(item => item.id !== id);
  }
</script>

<main>
  <div class="wrapper">
  {#each data as item}
    <div class="item">{item.name}
      <button on:click={() => remove(item.id)}>삭제</button>
    </div>
  {/each}
  </div>
  <button on:click={add}>추가</button>
  <button on:click={modify}>변경</button>
</main>

<style>
  .wrapper {
    width: 500px;
    margin: 20px auto;
  }

  .item {
    border: 1px solid #333;
    padding: 10px;
    border-radius: 5px;
  }

  .item + .item {
    margin-top: 10px;
  }

  button {
    display: block;
    margin: 20px auto;
    padding: 10px 20px;
    border: 1px solid #333;
    border-radius: 5px;
    background: #fff;
    cursor: pointer;
  }
</style>