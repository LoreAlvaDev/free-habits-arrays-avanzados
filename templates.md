# Templates

```html
<div id="filterModal" class="modal">
  <div class="modal-content">
    <div class="modal-header">
      <h3>Filtrar</h3>
      <button class="close-modal" data-modal="filterModal">&times;</button>
    </div>
    <div class="modal-body">
      <form id="filterForm">
        <div class="form-group">
          <label for="filterBy">Filtrar por</label>
          <select id="filterBy" name="filterBy">
            <option value="all">Todos</option>
            <option value="daily">Diario</option>
            <option value="weekly">Semanal</option>
          </select>
        </div>
        <div class="modal-footer">
          <button class="btn-secondary" type="button" data-modal="filterModal">
            Cancelar
          </button>
          <button class="btn-primary" type="submit" id="filterBtn">
            Filtrar
          </button>
        </div>
      </form>
    </div>
  </div>
</div>
```

```js
class FilterState {
  #filters = {
    frequency: "all",
    streakStatus: "all",
    minStreak: 0,
    search: "",
  };

  get filters() {
    return { ...this.#filters };
  }

  setFilter(key, value) {
    this.#filters[key] = value;
  }

  setFilters(newFilters) {
    this.#filters = { ...this.#filters, ...newFilters };
  }

  reset() {
    this.#filters = {
      frequency: "all",
      streakStatus: "all",
      minStreak: 0,
      search: "",
    };
  }
}
```

```js
class HabitService {
  #applyFilters(habits, filters) {
    return habits.filter((habit) => {
      // Filtro por frecuencia
      if (
        filters.frequency !== "all" &&
        habit.frequency !== filters.frequency
      ) {
        return false;
      }

      // Filtro por estado de racha
      const streak = habit.calculateStreak();
      if (filters.streakStatus === "active" && streak === 0) {
        return false;
      }
      if (filters.streakStatus === "inactive" && streak > 0) {
        return false;
      }

      // Filtro por racha mínima
      if (streak < filters.minStreak) {
        return false;
      }

      // Filtro por búsqueda
      if (
        filters.search &&
        !habit.name.toLowerCase().includes(filters.search.toLowerCase())
      ) {
        return false;
      }

      return true;
    });
  }
}
```
