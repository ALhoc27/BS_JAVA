# IntelliJ IDEA и GitHub

## Загрузить проект из IntelliJ IDEA в новый репозиторию GitHub



{% tabs %}
{% tab title="С помощью терминала в IntelliJ IDEA " %}
**1.** [Создание нового репозитория на **GitHub**](#user-content-fn-1)[^1]

**2.** [Открыть терминал в **IntelliJ IDEA**](#user-content-fn-2)[^2]

**3.** Инициализация Git и подключение удалённого репозитория:

<pre class="language-bash" data-full-width="true"><code class="lang-bash"><a data-footnote-ref href="#user-content-fn-3">git init</a>  // Инициализировать Git, если это ещё не сделано
<a data-footnote-ref href="#user-content-fn-4">git add .</a> // Добавить файлы в отслеживание Git
<a data-footnote-ref href="#user-content-fn-5">git commit -m "Initial commit"</a> //  Сделать первый коммит
<a data-footnote-ref href="#user-content-fn-6">git remote add origin https://github.com/ALhoc27/BS_GIT</a> // добавления удалённого репозитория к вашему локальному проекту

</code></pre>

**4.** Загрузить проект в новый репозиторий на **GitHub**

<pre class="language-bash"><code class="lang-bash"><a data-footnote-ref href="#user-content-fn-7">git push -u origin master</a> // Отправить (push) коммит в удалённый репозиторий
</code></pre>
{% endtab %}

{% tab title="Графическим интерфейсом IntelliJ IDEA" %}
<figure><img src="../../.gitbook/assets/Снимок экрана 2024-09-22 в 13.16.23.png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

## Загрузить проект из GitHub в IntelliJ IDEA

**1.** [Скопируйте URL репозитория на GitHub](#user-content-fn-8)[^8]

**2.** [Откройте IntelliJ IDEA](#user-content-fn-9)[^9]

**3.** [Клонирование репозитория](#user-content-fn-10)[^10]

[^1]: **1.** Войдите в свой аккаунт **GitHub**.

    **2.** Перейдите на вкладку **Repositories** и нажмите кнопку **New**.

    **3.** Нажмите **Create repository**

[^2]: В **IntelliJ IDEA** перейди в терминал через меню `View` → `Tool Windows` → `Terminal` или нажми <mark style="color:orange;">**`Alt+F12`**</mark>

[^3]: **IntelliJ IDEA** поддерживает множество систем контроля версий (VCS), и для того чтобы работать с **Git**, нужно его инициализировать. \
    Это создаст папку `.git`, которая будет отслеживать изменения в проекте.

[^4]: **Git** отслеживает только те файлы, которые были явно добавлены в систему контроля версий. \
    Этим шагом вы добавляете все файлы в индексацию для следующего коммита.

[^5]: Коммит фиксирует текущую версию файлов в проекте

[^6]: [Скопируйте URL репозитория на GitHub](#user-content-fn-11)[^11]\


    `git remote add` — это команда Git, которая позволяет добавить новый удалённый репозиторий в ваш проект.

    `origin` — это имя удалённого репозитория, которое присваивается по умолчанию. Это просто ярлык, который используется для того, чтобы ссылаться на удалённый репозиторий. Вместо того, чтобы каждый раз указывать полный URL репозитория, вы можете использовать это имя. Обычно `origin` используется для обозначения основного репозитория, с которым вы работаете. (удалённый репозиторий назвать можно как угодно)

[^7]: Команда `-u origin master` задаёт ветку `master` как основную для отправки изменений. В будущем, для пуша будет достаточно использовать просто команду `git push`.

[^8]: Зайдите на страницу нужного репозитория на **GitHub** и и скопируйте URL репозитория

    <img src="broken-reference" alt="" data-size="original">

[^9]: ⚫︎ Если у вас уже запущен другой проект, выберите **File → Close Project**.\\

    ⚫︎ Теперь вы должны увидеть начальный экран IntelliJ IDEA.

[^10]: ⚫︎ На начальном экране выберите **Get from VCS** или перейдите в меню **File → New → Project from Version Control**.

    \
    ⚫︎ В поле **URL** вставьте скопированный URL репозитория с GitHub.

    \
    ⚫︎ Укажите папку, в которую будет склонирован проект, и нажмите **Clone**.
