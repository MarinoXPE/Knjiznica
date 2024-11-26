<template>
  <q-page padding>
    <div class="q-pa-md">
      <q-input
        v-model="searchQuery"
        label="Unesite naziv ili autora knjige"
        outlined
        clearable
      />

      <div class="q-my-md">
        <q-checkbox v-model="searchByTitle" label="Pretraži po naslovu" />
        <q-checkbox v-model="searchByAuthor" label="Pretraži po autoru" />
      </div>

      <q-btn label="Traži" color="primary" @click="performSearch" />

      <q-table
        v-if="filteredBooks.length"
        :rows="filteredBooks"
        :columns="columns"
        row-key="id"
        title="Rezultati Pretraživanja"
        class="q-mt-md"
      />
    </div>
  </q-page>
</template>


<script>
import { ref } from 'vue';

export default {
  setup() {
    const searchQuery = ref('');
    const searchByTitle = ref(true);
    const searchByAuthor = ref(false);

    const columns = [
      { name: 'id', label: 'ID', align: 'left', field: row => row.id },
      { name: 'naslov', label: 'Naslov', align: 'left', field: row => row.naslov },
      { name: 'autor', label: 'Autor', align: 'left', field: row => row.autor },
      { name: 'opis', label: 'Opis', align: 'left', field: row => row.opis },
      { name: 'stanje', label: 'Stanje', align: 'right', field: row => row.stanje }
    ];

    const books = [
        { id: 1, naslov: 'Razvoj interaktivnih web-aplikacija', autor: 'Vlatka Davidović', opis: 'Temeljit uvod u suvremene tehnologije i metodologije koje se koriste u razvoju dinamičnih i korisnički interaktivnih web-aplikacija.', stanje: 1 },
        { id: 2, naslov: 'The Art of War', autor: 'Sun Tzu', opis: 'Drevna kineska vojna rasprava koja datira iz razdoblja kasnog proljeća i jeseni.', stanje: 32 },
        { id: 3, naslov: 'Six Secret Teachings', autor: 'Jiang Ziya', opis: 'Rasprava o civilnoj i vojnoj strategiji koja se tradicionalno pripisuje Lü Shangu, glavnom generalu kralja Wena od Zhoua, osnivaču dinastije Zhou, oko jedanaestog stoljeća prije Krista.', stanje: 7 },
        { id: 4, naslov: 'Crvenkapica', autor: 'Braća Grimm', opis: 'Bajka o mladoj djevojci i lukavom vuku.', stanje: 15 },
        { id: 5, naslov: 'Carevo novo ruho', autor: 'Hans Christian Andersen', opis: 'Tašti car koji se razotkriva pred svojim podanicima.', stanje: 500 }
      ]
const filteredBooks = ref([]);

const performSearch = () => {
  if (!searchQuery.value) {
    filteredBooks.value = [];
    return;
  }
  filteredBooks.value = books.filter(book => {
    const matchesTitle = searchByTitle.value && book.naslov.toLowerCase().includes(searchQuery.value.toLowerCase());
    const matchesAuthor = searchByAuthor.value && book.autor.toLowerCase().includes(searchQuery.value.toLowerCase());
    return matchesTitle || matchesAuthor;
  });
};

return {
  searchQuery,
  searchByTitle,
  searchByAuthor,
  columns,
  books,
  filteredBooks,
  performSearch
};
}
};
</script>