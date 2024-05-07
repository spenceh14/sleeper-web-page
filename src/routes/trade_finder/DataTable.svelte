<script>
import DataTable, { Head, Body, Row, Cell } from '@smui/data-table';
export let position;
export let pos_data;

</script>
<div class="holder" style='margin-left:50px'>

<h4>{position}</h4>

<DataTable>
    <Head>
        <Row>
            <Cell>Rank</Cell>
            {#each Object.keys(pos_data[0]) as col_key}
            <Cell> {col_key}</Cell>
            {/each}
        </Row>
    </Head>
    <Body>
        {#each pos_data as row, i}
      <Row>
        <Cell>{i+1}</Cell>
        {#each Object.values(row) as value}
          <Cell>{value}</Cell>
        {/each}
      </Row>
        {/each}
    </Body>
</DataTable>

</div>