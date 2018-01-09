---
lang: pl

table_data:
  - field_name: agency_id
    details:
      - ID: 1
        required: false
        tags: []
        text: |
          Pole **agency_id** zawiera unikalny identyfikator reprezentujący placówkę odpowiedzialną za rozkłady. Jeden plik może zawierać dane wielu organizatorów/spółek. **agency_id** jest unikatowe w skali pliku. Pole jest opcjonalne w przypadku plików z tylko jedną placówką.
  - field_name: agency_name
    details:
      - ID: 2
        required: true
        tags: []
        text: |
          Pole **agency_name** zawiera pełną nazwę placówki odpowiedzialnej za organizowanie przejazdów na liniach. Mapy Google będą wyświetlały tę nazwę.
  - field_name: agency_url
    details:
      - ID: 3
        required: true
        tags: []
        text: |
          Pole **agency_url** zawiera adres URL strony placówki. Pole musi być poprawnym adresem URL który zawiera **http**:// lub **https**://, a wszelkie znaki specjalne powinny być odpowiednio zakodowane. Zobacz http://www.w3.org/Addressing/URL/4_URI_Recommentations.html dla pełnego opisu jak stworzyć poprawny adres URL.
  - field_name: agency_timezone
    details:
      - ID: 4
        required: true
        tags: []
        text: |
          Pole **agency_timezone** zawiera informacje o podstawowej strefie czasowej placówki. Strefa czasowa nigdy nie zawiera spacji, lecz może zawierać podkreślnik. Proszę odwołać się do http://en.wikipedia.org/wiki/List_of_tz_zones po listę prawidłowych wartości. Jeśli w pliku znajduje się więcej niż jedna placówka, każda musi mieć zdefiniowanę tę samę strefę czasową.
  - field_name: agency_lang
    details:
      - ID: 5
        required: false
        tags: []
        text: |
          Pole **agency_lang** zawiera kod ISO 639-1 podstawowego języka, jakim posługuje się spółka. Wielkość liter nie ma znaczenia (zarówno pl jak i PL są wartościami poprawnymi). To ustawienie definiuje sposób kapitalizacji tekstów oraz innych opcji zależnych od języka. Proszę odwołać się do http://www.loc.gov/standards/iso639-2/php/code_list.php po listę prawidłowych wartości.
  - field_name: agency_phone
    details:
      - ID: 6
        required: false
        tags: []
        text: |
          Pole **agency_phone** zawiera numer telefonu do danej placówki. Pole jest tekstem prezentującym numer telefonu w sposób, jaki jest domyślny dla placówki. **agency_phone** może i powinno zawierać znaki interpunkcyjne w celu oddzielenia róznych grup cyfr. Wybieralny tekst (np. "503-238-RIDE" TriMetu) jest dozwolony, ale pole nie powinno zawierać żadneego dodatkowego opisu.
  - field_name: agency_fare_url
    details:
      - ID: 7
        required: false
        tags: []
        text: |
          Pole **agency_fare_url** definiuje adres URL, gdzie pasażer może zakupić bilet, lub przeczytać informacje o taryfie biletowej. Pole musi być poprawnym adresem URL który zawiera **http**:// lub **https**://, a wszelkie znaki specjalne powinny być odpowiednio zakodowane. Zobacz http://www.w3.org/Addressing/URL/4_URI_Recommentations.html dla pełnego opisu jak stworzyć poprawny adres URL.
  - field_name: agency_email
    details:
      - ID: 8
        required: false
        tags: []
        text: |
          Pole **agency_email** definiuje pojedyńczy adres email aktywnie monitorowany przez biuro obsługi klienta placówki. Ten adres email jest traktowany jako bezpośredni punkt kontaktu z biurem obsługi klienta organizatora/spółki.
---
Plik: **Wymagany**

<div class="table-wrapper">
  <table class="recommendation">
    <thead>
      <tr>
        <th>Nazwa Pola</th>
        <th>Wymagane</th>
        <th>Opis</th>
      </tr>
    </thead>
    <tbody>
    {% for field in page.table_data %}
      {% for detail in field.details %}
      <tr id="{{ page.slug }}_{{ detail.ID }}" class="anchor-row{% if forloop.first %} field-row{% endif %}{% for tag in detail.tags %} {{ tag }}{% endfor %}">
        <td>{% if forloop.first %}<code>{{ field.field_name }}</code>{% endif %}</td>
        <td>{% if detail.required %}Wymagane{% else %}Opcjonalne{% endif %}</td>
        <td>{{ detail.text | markdownify }}{% if detail.example_table %}<div class="table-wrapper">{{ detail.example_table }}</div>{% endif %}</td>
      </tr>
      {% endfor %}
    {% endfor %}
    </tbody>
  </table>
</div>