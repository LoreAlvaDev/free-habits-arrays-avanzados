# Notes

```js
// Lo que ya conoces del proyecto FreeHabits
habits.push(newHabit); // Agregar
habits.find((h) => h.id === id); // Buscar
habits.findIndex((h) => h.id); // Encontrar índice
habits.splice(index, 1); // Eliminar
habits.forEach((h) => render(h)); // Iterar
habits.map((h) => h.name); // Transformar
logs.sort((a, b) => b - a); // Ordenar
```

### Mapa de Métodos

| Método          | Retorna                | Muta Original | Uso Principal                |
| --------------- | ---------------------- | ------------- | ---------------------------- |
| `forEach`       | `undefined`            | No            | Ejecutar acción por elemento |
| `map`           | `Array` nuevo          | No            | Transformar elementos        |
| `filter`        | `Array` nuevo          | No            | Seleccionar elementos        |
| `reduce`        | Cualquier valor        | No            | Agregar/acumular             |
| `find`          | Elemento o `undefined` | No            | Buscar primer coincidencia   |
| `findIndex`     | Índice o `-1`          | No            | Buscar posición              |
| `some`          | `boolean`              | No            | ¿Existe al menos uno?        |
| `every`         | `boolean`              | No            | ¿Todos cumplen?              |
| `includes`      | `boolean`              | No            | ¿Contiene valor?             |
| `flat`          | `Array` nuevo          | No            | Aplanar anidados             |
| `flatMap`       | `Array` nuevo          | No            | Map + flat                   |
| `sort`          | `Array` mismo          | **Sí**        | Ordenar                      |
| `push/pop`      | Longitud/Elemento      | **Sí**        | Agregar/quitar final         |
| `shift/unshift` | Elemento/Longitud      | **Sí**        | Agregar/quitar inicio        |
| `splice`        | `Array` eliminados     | **Sí**        | Modificar en posición        |
