<template>
  <div class="home">
    <section class="hero">
      <h1 class="name-home">Православный магазин</h1>
      <p>Иконы, книги, крестики и церковная утварь. Всё для духовной жизни.</p>
      <router-link to="/products" class="btn btn-primary">Перейти в каталог</router-link>
    </section>

    <section class="features">
      <div class="feature">
        <h3> Освящённые товары</h3>
        <p>Работаем только с проверенными мастерскими и издательствами</p>
      </div>
      <div class="feature">
        <h3> Бережная доставка</h3>
        <p>Надёжная упаковка и отправка по всей России</p>
      </div>
      <div class="feature">
        <h3> Личный кабинет</h3>
        <p>История заказов, избранное и быстрое оформление</p>
      </div>
    </section>
  </div>
</template>

<style scoped>

.home {
  padding: 2rem 0;
  text-align: center;
  font-family: 'AkathistosFont';
}

.name-home{

}

.hero {
  background: var(--surface);
  padding: 4rem 2rem;
  border-radius: var(--radius);
  box-shadow: var(--shadow);
  margin-bottom: 3rem;
}

.hero h1 {
    font-family: 'AkathistosFont', sans-serif;
  font-size: 2.5rem;
  color: var(--primary);
  margin-bottom: 1rem;
}

.hero p {
  font-size: 1.2rem;
  color: var(--text-light);
  margin-bottom: 2rem;
}

.features {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
}

.feature {
  background: var(--surface);
  padding: 1.5rem;
  border-radius: var(--radius);
  box-shadow: var(--shadow);
  transition: transform 0.2s ease;
}

.feature:hover {
  transform: translateY(-4px);
}

.feature h3 {
  margin-bottom: 0.5rem;
  color: var(--primary);
}

/* Кнопка (если не объявлена в глобальном style.css) */
.btn {
  display: inline-block;
  padding: 0.8rem 2rem;
  border-radius: var(--radius);
  text-decoration: none;
  font-weight: 500;
  cursor: pointer;
  transition: background 0.2s;
  border: none;
}

.btn-primary {
  background: var(--primary);
  color: #fff;
}

.btn-primary:hover {
  background: var(--primary-hover);
}
</style>