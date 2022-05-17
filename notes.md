##handlebars

sintaxe de html normal + boostrap (opc)

para iniciar:

```
app.engine(
  'hbs',
  exphbs.engine({
    defaultLayout: 'main',
    extname: '.hbs',
  })
);

app.set('view engine', 'hbs');
```

para escutar uma rota (ex: localhost:3000/):

```
app.get('/', (req, res) => {
  res.render('home', {
    posts: [
      {
        author: 'Janith Kasun',
        image: 'https://picsum.photos/500/500',
        comments: [
          'This is the first comment',
          'This is the second comment',
          'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum nec fermentum ligula. Sed vitae erat lectus.',
        ],
      },
      {
        author: 'John Doe',
        image: 'https://picsum.photos/500/500?2',
        comments: [],
      },
    ],
  });
});
```

\*\*obj após o 'home' indica um obj que sera passado como parametro para a rota, no caso um array de obj chamado posts

sintaxe if
{{#if condicao}}

{{else}}

{{/if}}

sintaxe each

{{#each}}
{{/each}}

dentro do each da para acessar os parametros do obj atraves do this
ex: this.author

```{{#each posts}}

  <div class="col-lg-7" style="margin-top: 50px;">
    <div class="card">
      <img src="{{this.image}}" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">Posted by {{this.author}}</h5>

        {{#if this.comments}}
          <ul class="list-group">
            {{#each this.comments}}
              <li class="list-group-item">{{this}}</li>
            {{/each}}
          </ul>
        {{else}}
          <ul class="list-group">
            <li class="list-group-item">Be first to comment on this post</li>
          </ul>
        {{/if}}
      </div>
    </div>

  </div>
{{/each}}
```
