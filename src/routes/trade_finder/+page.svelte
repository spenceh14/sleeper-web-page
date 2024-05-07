<script>
import DataTable, { Head, Body, Row, Cell } from '@smui/data-table';
let wr_scores = [{'Owner': 'mfavs1134', 'Total_points': '1533.18', 'Average_age': '24.95'}, {'Owner': 'jbear3', 'Total_points': '1483.22', 'Average_age': '27.99'}, {'Owner': 'spenceh14', 'Total_points': '1386.36', 'Average_age': '24.11'}, {'Owner': 'petrielloma', 'Total_points': '1318', 'Average_age': '24.79'}, {'Owner': 'alongsy1hundo', 'Total_points': '1295.8', 'Average_age': '24.69'}, {'Owner': 'gmelzen', 'Total_points': '1256.2', 'Average_age': '26.84'}, {'Owner': 'nickmikes13', 'Total_points': '1248.3', 'Average_age': '25.91'}, {'Owner': 'JHOCKENBERRY', 'Total_points': '1217.2', 'Average_age': '28.39'}, {'Owner': 'donofrio32', 'Total_points': '1182.4', 'Average_age': '24.20'}, {'Owner': 'uconn777', 'Total_points': '1133.06', 'Average_age': '27.76'}, {'Owner': 'JayBonesy6', 'Total_points': '923.4', 'Average_age': '23.74'}, {'Owner': 'Tmo2222', 'Total_points': '767.58', 'Average_age': '24.88'}]
let len = Object.values(wr_scores)[0].length;
</script>
<div class="holder">

<h4>Wide Receivers</h4>

<DataTable>
    <Head>
        <tr>
            {#each Object.keys(wr_scores[0]) as col_key}
            <td> {col_key}</td>
            {/each}
        </tr>
    </Head>
    <Body>
        {#each wr_scores as row}
      <Row>
        {#each Object.values(row) as value}
          <Cell>{value}</Cell>
        {/each}
      </Row>
        {/each}
    </Body>
</DataTable>

</div>