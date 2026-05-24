<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>DentalCare Clinic</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Arial, sans-serif;
      background: #f7fbff;
      color: #17324d;
      line-height: 1.6;
    }

    .language-switcher {
      position: fixed;
      top: 18px;
      right: 18px;
      z-index: 1000;
      background: white;
      padding: 8px;
      border-radius: 30px;
      box-shadow: 0 8px 25px rgba(0, 80, 130, 0.15);
      display: flex;
      gap: 6px;
    }

    .language-switcher label {
      cursor: pointer;
      padding: 7px 12px;
      border-radius: 20px;
      font-size: 13px;
      font-weight: bold;
      color: #2077a8;
      transition: 0.3s;
    }

    input[type="radio"] {
      display: none;
    }

    #en:checked ~ .language-switcher label[for="en"],
    #ru:checked ~ .language-switcher label[for="ru"],
    #hy:checked ~ .language-switcher label[for="hy"] {
      background: #2bb3d9;
      color: white;
    }

    .lang { display: none; }
    #en:checked ~ .page .en { display: inline; }
    #ru:checked ~ .page .ru { display: inline; }
    #hy:checked ~ .page .hy { display: inline; }

    .page {
      overflow: hidden;
    }

    header {
      min-height: 100vh;
      background:
        linear-gradient(120deg, rgba(9, 84, 132, 0.82), rgba(43, 179, 217, 0.65)),
        url('https://images.unsplash.com/photo-1606811971618-4486d14f3f99?auto=format&fit=crop&w=1600&q=80');
      background-size: cover;
      background-position: center;
      color: white;
      display: flex;
      align-items: center;
      padding: 40px 8%;
    }

    nav {
      position: absolute;
      top: 25px;
      left: 8%;
      display: flex;
      align-items: center;
      gap: 35px;
    }

    .logo {
      font-size: 26px;
      font-weight: 800;
      letter-spacing: 1px;
    }

    .logo span {
      color: #bff5ff;
    }

    .hero {
      max-width: 670px;
      animation: fadeUp 1.1s ease;
    }

    .hero h1 {
      font-size: clamp(42px, 7vw, 78px);
      line-height: 1.05;
      margin-bottom: 22px;
    }

    .hero p {
      font-size: 19px;
      margin-bottom: 35px;
      max-width: 560px;
      color: #edfaff;
    }

    .buttons {
      display: flex;
      gap: 15px;
      flex-wrap: wrap;
    }

    .btn {
      text-decoration: none;
      padding: 15px 26px;
      border-radius: 40px;
      font-weight: bold;
      transition: 0.3s;
      display: inline-block;
    }

    .btn-primary {
      background: white;
      color: #0f7199;
    }

    .btn-primary:hover {
      transform: translateY(-4px);
      box-shadow: 0 12px 25px rgba(255,255,255,0.25);
    }

    .btn-secondary {
      border: 2px solid white;
      color: white;
    }

    .btn-secondary:hover {
      background: white;
      color: #0f7199;
    }

    section {
      padding: 90px 8%;
    }

    .section-title {
      text-align: center;
      margin-bottom: 55px;
    }

    .section-title h2 {
      font-size: clamp(32px, 5vw, 48px);
      color: #123c61;
      margin-bottom: 12px;
    }

    .section-title p {
      color: #607d95;
      max-width: 620px;
      margin: auto;
      font-size: 17px;
    }

    .about {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 55px;
      align-items: center;
    }

    .about img {
      width: 100%;
      border-radius: 30px;
      box-shadow: 0 20px 45px rgba(27, 105, 145, 0.18);
      animation: float 4s ease-in-out infinite;
    }

    .about-text h2 {
      font-size: 42px;
      margin-bottom: 20px;
      color: #123c61;
    }

    .about-text p {
      color: #5f7487;
      margin-bottom: 18px;
      font-size: 17px;
    }

    .features {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 25px;
    }

    .feature-card,
    .service-card,
    .doctor-card,
    .contact-box {
      background: white;
      border-radius: 25px;
      padding: 30px;
      box-shadow: 0 12px 35px rgba(22, 94, 140, 0.09);
      transition: 0.35s;
    }

    .feature-card:hover,
    .service-card:hover,
    .doctor-card:hover {
      transform: translateY(-10px);
    }

    .icon {
      width: 62px;
      height: 62px;
      background: linear-gradient(135deg, #2bb3d9, #67e0f6);
      border-radius: 18px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 30px;
      margin-bottom: 20px;
    }

    .feature-card h3,
    .service-card h3,
    .doctor-card h3 {
      font-size: 22px;
      margin-bottom: 12px;
      color: #123c61;
    }

    .feature-card p,
    .service-card p,
    .doctor-card p {
      color: #617789;
    }

    .services {
      background: #eaf8fc;
    }

    .service-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 25px;
    }

    .service-card img {
      width: 100%;
      height: 190px;
      object-fit: cover;
      border-radius: 20px;
      margin-bottom: 20px;
    }

    .doctors {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 25px;
    }

    .doctor-card {
      text-align: center;
    }

    .doctor-card img {
      width: 150px;
      height: 150px;
      object-fit: cover;
      border-radius: 50%;
      margin-bottom: 20px;
      border: 6px solid #e4f8fd;
    }

    .stats {
      background: linear-gradient(135deg, #0f7199, #2bb3d9);
      color: white;
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 25px;
      text-align: center;
    }

    .stat h3 {
      font-size: 42px;
      margin-bottom: 6px;
    }

    .stat p {
      color: #e6fbff;
    }

    .contact {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 35px;
      align-items: center;
    }

    form {
      display: grid;
      gap: 16px;
    }

    input,
    textarea,
    select {
      width: 100%;
      padding: 15px 18px;
      border-radius: 14px;
      border: 1px solid #cde5ef;
      font-size: 15px;
      outline: none;
    }

    input:focus,
    textarea:focus,
    select:focus {
      border-color: #2bb3d9;
    }

    textarea {
      min-height: 125px;
      resize: vertical;
    }

    button {
      border: none;
      background: #2bb3d9;
      color: white;
      padding: 16px;
      border-radius: 40px;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      background: #0f7199;
      transform: translateY(-3px);
    }

    .contact-info p {
      margin-bottom: 14px;
      color: #5f7487;
      font-size: 17px;
    }

    footer {
      background: #0d2b44;
      color: white;
      text-align: center;
      padding: 30px 8%;
    }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(35px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-12px); }
    }

    @media (max-width: 900px) {
      .about,
      .features,
      .service-grid,
      .doctors,
      .stats,
      .contact {
        grid-template-columns: 1fr;
      }

      header {
        padding-top: 120px;
      }

      nav {
        left: 5%;
      }

      .language-switcher {
        top: 70px;
        right: 5%;
      }
    }
  </style>
</head>
<body>
  <input type="radio" name="language" id="en" checked>
  <input type="radio" name="language" id="ru">
  <input type="radio" name="language" id="hy">

  <div class="language-switcher">
    <label for="en">EN</label>
    <label for="ru">RU</label>
    <label for="hy">HY</label>
  </div>

  <div class="page">
    <header>
      <nav>
        <div class="logo">Dental<span>Care</span></div>
      </nav>

      <div class="hero">
        <h1>
          <span class="lang en">Beautiful Smile, Healthy Life</span>
          <span class="lang ru">Красивая улыбка, здоровая жизнь</span>
          <span class="lang hy">Գեղեցիկ ժպիտ, առողջ կյանք</span>
        </h1>
        <p>
          <span class="lang en">Modern dental clinic with gentle care, advanced technology and professional doctors for your whole family.</span>
          <span class="lang ru">Современная стоматологическая клиника с бережным уходом, новыми технологиями и опытными врачами для всей семьи.</span>
          <span class="lang hy">Ժամանակակից ստոմատոլոգիական կլինիկա՝ նուրբ մոտեցմամբ, նոր տեխնոլոգիաներով և փորձառու բժիշկներով ամբողջ ընտանիքի համար։</span>
        </p>
        <div class="buttons">
          <a href="#contact" class="btn btn-primary">
            <span class="lang en">Book Appointment</span>
            <span class="lang ru">Записаться</span>
            <span class="lang hy">Գրանցվել</span>
          </a>
          <a href="#services" class="btn btn-secondary">
            <span class="lang en">Our Services</span>
            <span class="lang ru">Наши услуги</span>
            <span class="lang hy">Մեր ծառայությունները</span>
          </a>
        </div>
      </div>
    </header>

    <section>
      <div class="about">
        <img src="https://images.unsplash.com/photo-1629909613654-28e377c37b09?auto=format&fit=crop&w=1000&q=80" alt="Dental clinic room">
        <div class="about-text">
          <h2>
            <span class="lang en">Care You Can Trust</span>
            <span class="lang ru">Забота, которой можно доверять</span>
            <span class="lang hy">Խնամք, որին կարող եք վստահել</span>
          </h2>
          <p>
            <span class="lang en">We believe dental treatment should be comfortable, safe and stress-free. Our clinic combines friendly service with high-quality medical standards.</span>
            <span class="lang ru">Мы верим, что лечение зубов должно быть комфортным, безопасным и без стресса. Наша клиника сочетает дружелюбный сервис и высокие медицинские стандарты.</span>
            <span class="lang hy">Մենք հավատում ենք, որ ատամնաբուժական բուժումը պետք է լինի հարմարավետ, անվտանգ և առանց սթրեսի։ Մեր կլինիկան համադրում է հոգատար սպասարկումն ու բարձր բժշկական չափանիշները։</span>
          </p>
          <p>
            <span class="lang en">From routine checkups to smile design, we help you feel confident every time you smile.</span>
            <span class="lang ru">От обычного осмотра до дизайна улыбки — мы помогаем вам уверенно улыбаться каждый день.</span>
            <span class="lang hy">Սովորական զննումից մինչև ժպիտի ձևավորում՝ մենք օգնում ենք ձեզ ժպտալ վստահությամբ։</span>
          </p>
        </div>
      </div>
    </section>

    <section>
      <div class="section-title">
        <h2>
          <span class="lang en">Why Choose Us</span>
          <span class="lang ru">Почему выбирают нас</span>
          <span class="lang hy">Ինչու ընտրել մեզ</span>
        </h2>
      </div>
      <div class="features">
        <div class="feature-card">
          <div class="icon">🦷</div>
          <h3><span class="lang en">Modern Equipment</span><span class="lang ru">Современное оборудование</span><span class="lang hy">Ժամանակակից սարքավորումներ</span></h3>
          <p><span class="lang en">High-quality dental technology for accurate and comfortable treatment.</span><span class="lang ru">Качественные технологии для точного и комфортного лечения.</span><span class="lang hy">Բարձրորակ տեխնոլոգիաներ՝ ճշգրիտ և հարմարավետ բուժման համար։</span></p>
        </div>
        <div class="feature-card">
          <div class="icon">👩‍⚕️</div>
          <h3><span class="lang en">Experienced Doctors</span><span class="lang ru">Опытные врачи</span><span class="lang hy">Փորձառու բժիշկներ</span></h3>
          <p><span class="lang en">Our specialists provide careful treatment and personal attention.</span><span class="lang ru">Наши специалисты обеспечивают внимательное лечение и индивидуальный подход.</span><span class="lang hy">Մեր մասնագետներն ապահովում են ուշադիր բուժում և անհատական մոտեցում։</span></p>
        </div>
        <div class="feature-card">
          <div class="icon">✨</div>
          <h3><span class="lang en">Beautiful Results</span><span class="lang ru">Красивый результат</span><span class="lang hy">Գեղեցիկ արդյունք</span></h3>
          <p><span class="lang en">We focus on healthy teeth and naturally beautiful smiles.</span><span class="lang ru">Мы заботимся о здоровье зубов и естественно красивой улыбке.</span><span class="lang hy">Մենք հոգում ենք առողջ ատամների և բնական գեղեցիկ ժպիտի մասին։</span></p>
        </div>
      </div>
    </section>

    <section class="services" id="services">
      <div class="section-title">
        <h2><span class="lang en">Our Services</span><span class="lang ru">Наши услуги</span><span class="lang hy">Մեր ծառայությունները</span></h2>
        <p><span class="lang en">Complete dental care for adults and children.</span><span class="lang ru">Полный стоматологический уход для взрослых и детей.</span><span class="lang hy">Ամբողջական ատամնաբուժական խնամք մեծերի և երեխաների համար։</span></p>
      </div>

      <div class="service-grid">
        <div class="service-card">
          <img src="https://images.unsplash.com/photo-1609840114035-3c981b782dfe?auto=format&fit=crop&w=900&q=80" alt="Teeth whitening">
          <h3><span class="lang en">Teeth Whitening</span><span class="lang ru">Отбеливание зубов</span><span class="lang hy">Ատամների սպիտակեցում</span></h3>
          <p><span class="lang en">Safe whitening for a brighter and fresher smile.</span><span class="lang ru">Безопасное отбеливание для более яркой улыбки.</span><span class="lang hy">Անվտանգ սպիտակեցում՝ ավելի պայծառ ժպիտի համար։</span></p>
        </div>

        <div class="service-card">
          <img src="https://images.unsplash.com/photo-1588776814546-1ffcf47267a5?auto=format&fit=crop&w=900&q=80" alt="Dental treatment">
          <h3><span class="lang en">Dental Treatment</span><span class="lang ru">Лечение зубов</span><span class="lang hy">Ատամների բուժում</span></h3>
          <p><span class="lang en">Gentle treatment for cavities, pain and dental problems.</span><span class="lang ru">Бережное лечение кариеса, боли и других проблем.</span><span class="lang hy">Նուրբ բուժում կարիեսի, ցավի և այլ խնդիրների համար։</span></p>
        </div>

        <div class="service-card">
          <img src="https://images.unsplash.com/photo-1598256989800-fe5f95da9787?auto=format&fit=crop&w=900&q=80" alt="Dental consultation">
          <h3><span class="lang en">Consultation</span><span class="lang ru">Консультация</span><span class="lang hy">Խորհրդատվություն</span></h3>
          <p><span class="lang en">Professional examination and clear treatment plan.</span><span class="lang ru">Профессиональный осмотр и понятный план лечения.</span><span class="lang hy">Մասնագիտական զննում և հստակ բուժման պլան։</span></p>
        </div>
      </div>
    </section>

    <section>
      <div class="section-title">
        <h2><span class="lang en">Our Doctors</span><span class="lang ru">Наши врачи</span><span class="lang hy">Մեր բժիշկները</span></h2>
      </div>
      <div class="doctors">
        <div class="doctor-card">
          <img src="https://images.unsplash.com/photo-1559839734-2b71ea197ec2?auto=format&fit=crop&w=600&q=80" alt="Doctor">
          <h3>Dr. Anna Smith</h3>
          <p><span class="lang en">General Dentist</span><span class="lang ru">Стоматолог-терапевт</span><span class="lang hy">Ընդհանուր ստոմատոլոգ</span></p>
        </div>
        <div class="doctor-card">
          <img src="https://images.unsplash.com/photo-1622253692010-333f2da6031d?auto=format&fit=crop&w=600&q=80" alt="Doctor">
          <h3>Dr. David Brown</h3>
          <p><span class="lang en">Orthodontist</span><span class="lang ru">Ортодонт</span><span class="lang hy">Օրթոդոնտ</span></p>
        </div>
        <div class="doctor-card">
          <img src="https://images.unsplash.com/photo-1594824476967-48c8b964273f?auto=format&fit=crop&w=600&q=80" alt="Doctor">
          <h3>Dr. Maria Lee</h3>
          <p><span class="lang en">Cosmetic Dentist</span><span class="lang ru">Эстетический стоматолог</span><span class="lang hy">Էսթետիկ ստոմատոլոգ</span></p>
        </div>
      </div>
    </section>

    <section class="stats">
      <div class="stat"><h3>10+</h3><p><span class="lang en">Years Experience</span><span class="lang ru">Лет опыта</span><span class="lang hy">Տարի փորձ</span></p></div>
      <div class="stat"><h3>5k+</h3><p><span class="lang en">Happy Patients</span><span class="lang ru">Довольных пациентов</span><span class="lang hy">Գոհ պացիենտներ</span></p></div>
      <div class="stat"><h3>15</h3><p><span class="lang en">Specialists</span><span class="lang ru">Специалистов</span><span class="lang hy">Մասնագետներ</span></p></div>
      <div class="stat"><h3>24/7</h3><p><span class="lang en">Support</span><span class="lang ru">Поддержка</span><span class="lang hy">Աջակցություն</span></p></div>
    </section>

    <section id="contact">
      <div class="section-title">
        <h2><span class="lang en">Book Your Visit</span><span class="lang ru">Запишитесь на приём</span><span class="lang hy">Գրանցվեք այցի համար</span></h2>
        <p><span class="lang en">Send us a message and we will contact you soon.</span><span class="lang ru">Оставьте сообщение, и мы скоро свяжемся с вами.</span><span class="lang hy">Ուղարկեք հաղորդագրություն, և մենք շուտով կկապվենք ձեզ հետ։</span></p>
      </div>

      <div class="contact">
        <div class="contact-box">
          <form>
            <input type="text" placeholder="Name / Имя / Անուն" required>
            <input type="tel" placeholder="Phone / Телефон / Հեռախոս" required>
            <input type="email" placeholder="Email" required>
            <select>
              <option>Teeth Whitening / Отбеливание / Սպիտակեցում</option>
              <option>Dental Treatment / Лечение / Բուժում</option>
              <option>Consultation / Консультация / Խորհրդատվություն</option>
            </select>
            <textarea placeholder="Message / Сообщение / Հաղորդագրություն"></textarea>
            <button type="submit">
              <span class="lang en">Send Request</span>
              <span class="lang ru">Отправить заявку</span>
              <span class="lang hy">Ուղարկել հայտը</span>
            </button>
          </form>
        </div>

        <div class="contact-box contact-info">
          <h3><span class="lang en">Contact Information</span><span class="lang ru">Контактная информация</span><span class="lang hy">Կոնտակտային տվյալներ</span></h3>
          <br>
          <p>📍 Yerevan, Armenia</p>
          <p>📞 +374 00 000 000</p>
          <p>✉️ dentalcare@example.com</p>
          <p>🕒 Mon - Sat: 09:00 - 19:00</p>
        </div>
      </div>
    </section>

    <footer>
      <p>© 2026 DentalCare Clinic. All rights reserved.</p>
    </footer>
  </div>
</body>
</html>

