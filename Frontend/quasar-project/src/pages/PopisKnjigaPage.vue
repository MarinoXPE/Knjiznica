<template>
  <q-page padding>
    <!-- Naslov i popratni tekst -->
    <div class="text-center q-mb-md">
      <h1>Popis knjiga</h1>
      <p>Pregled svih dostupnih knjiga u knjižnici.</p>
    </div>

    <!-- Tablica s podacima knjiga -->
    <q-table
      :rows="books"
      :columns="columns"
      row-key="id"
      :filter="filter"
    >
    </q-table>
  </q-page>
</template>

<script>
export default {
  setup() {
    // Podaci o knjigama (bez slika)
    const books = [
      {
        id: 1,
        naslov: 'Razvoj interaktivnih web-aplikacija',
        autor: 'Vlatka Davidović',
        opis: 'Temeljit uvod u suvremene tehnologije i metodologije koje se koriste u razvoju dinamičnih i korisnički interaktivnih web-aplikacija.',
        slika: '', // Ovdje možete staviti praznu putanju ili ukloniti ovo polje
        stanje: 1
      },
      {
        id: 2,
        naslov: 'The Art of War',
        autor: 'Sun Tzu',
        opis: 'Drevna kineska vojna rasprava koja datira iz razdoblja kasnog proljeća i jeseni.',
        slika: '', // Ovdje možete staviti praznu putanju ili ukloniti ovo polje
        stanje: 32
      },
      {
        id: 3,
        naslov: 'Six Secret Teachings',
        autor: 'Jiang Ziya',
        opis: 'Rasprava o civilnoj i vojnoj strategiji koja se tradicionalno pripisuje Lü Shangu, glavnom generalu kralja Wena od Zhoua, osnivaču dinastije Zhou, oko jedanaestog stoljeća prije Krista.',
        slika: '', // Ovdje možete staviti praznu putanju ili ukloniti ovo polje
        stanje: 7
      },
{
        id: 4,
        naslov: 'Crvenkapica',
        autor: 'Braća Grimm',
        opis: 'Bajka o mladoj djevojci i lukavom vuku.',
        slika: '', // Ovdje možete staviti praznu putanju ili ukloniti ovo polje
        stanje: 15
      },
      {
        id: 5,
        naslov: 'Carevo novo ruho',
        autor: 'Hans Christian Andersen',
        opis: 'Tašti car koji se razotkriva pred svojim podanicima.',
        slika: '', // Ovdje možete staviti praznu putanju ili ukloniti ovo polje
        stanje: 500
      }
    ];

    // Kolone za tablicu
    const columns = [
      { name: 'id', label: 'ID', align: 'left', field: 'id' },
      { name: 'naslov', label: 'Naslov', align: 'left', field: 'naslov' },
      { name: 'autor', label: 'Autor', align: 'left', field: 'autor' },
      { name: 'opis', label: 'Opis', align: 'left', field: 'opis' },
      { name: 'slika', label: 'Slika', align: 'center', field: 'slika', format: val => '' }, // Bez prikaza slike
      { name: 'stanje', label: 'Stanje', align: 'center', field: 'stanje' }
    ];

    // Filtriranje (opcionalno)
    const filter = '';

    return {
      books,
      columns,
      filter
    };
  }
};
</script>

<style scoped>
.q-page {
  padding: 20px;
}

.text-center {
  text-align: center;
}

.q-mb-md {
  margin-bottom: 20px;
}
.q-table {
  margin-top: 20px;
}
</style>