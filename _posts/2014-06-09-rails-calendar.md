---
layout: post
title:  "[OUT OF DATE] Criar agenda de compromissos usando Rails 4"
date:   2014-06-09
---

Uma forma muito legal de agregar uma agenda de compromissos ou eventos no seu projeto é utilizando um calendário. No Ruby on Rails é muito simples fazer isso com a ajuda da gem **table_builder**.

Crie um novo projeto e gere o modelo de compromisso.

{% highlight default %}
$ rails new AgendaDeCompromissos
$ rails g scaffold Compromisso titulo:string texto:text date:date
$ rake db:migrate
{% endhighlight %}

Instale a gem table_builder, adicionando na Gemfile:
{% highlight default %}
gem "watu_table_builder", :require => "table_builder"
{% endhighlight %}

Depois, no terminal digite:
{% highlight default %}
$ bundle install
{% endhighlight %}

Em view/compromissos/index.html.erb coloque o calendário: 
{% highlight erb %}
<div id="calendar">
	<%= calendar_for(@compromissos) do |t| %>
	<%= t.head('DOM','SEG', 'TER', 'QUA', 'QUI', 'SEX', 'SAB') %>
	<%= t.day do |day, compromissos| %>
	<%= day.day %>
	<% compromissos.each do |compromisso| %>
	<%= h(compromisso.titulo) %>
	<% end %>
	<% end %>
	<% end %>
</div>
<%= link_to 'Novo Compromisso', new_compromisso_path %>
{% endhighlight %}

Crie um arquivo css para definir o estilo do calendário,
assets/stylesheets/calendar.css:
{% highlight css %}
#calendar table {
border-collapse: collapse;
width: 100%;
}

#calendar td,
#calendar th {
font-family: "Lucida Grande",arial,helvetica,sans-serif;
font-size: 10px;
padding: 6px;
border: 1px solid #999;
}

#calendar th {
background: #DDD;
color: #666;
text-align: center;
width: 14.2857142857143%;
}

#calendar td {
background: #FFF;
color: #777;
height: 80px;
vertical-align: top;
font-size: 16px;
}

#calendar .notmonth {
color: #CCC;
}

#calendar #month {
margin: 0;
padding-top: 10px;
padding-bottom: 10px;
text-align: center;
}

#calendar #month a, #calendar #month a:hover {
text-decoration: none;
padding: 0 10px;
color: #999;
}

#calendar .today {
background-color: #D7F2FF;
}

#calendar ul {
margin: 0;
margin-top: 5px;
padding: 0;
list-style: none;
}

#calendar li {
margin: 0;
padding: 0;
font-size: 11px;
text-align: center;
}
{% endhighlight %}

Nessa altura já temos o calendário com estilo criado:
<figure>
	<img src="../assets/img/calendar1.png">
</figure>

Agora setamos o compromisso em app/controllers/compromissos_controller.rb para receber a data presente:

{% highlight ruby %}
def index
	@compromissos = Compromisso.all
	@date = params[:month] ? Date.parse(params[:month]) : Date.today
end
{% endhighlight %}

Para colocar o mês e o ano na view e incluir os botões de editar e deletar, fazemos o seguinte em app/views/projects/index.html.erb:

{% highlight erb %}
<div id="calendar">
	<%= calendar_for(@compromissos) do |t| %>
	<%= t.head('DOM','SEG', 'TER', 'QUA', 'QUI', 'SEX', 'SAB') %>
	<%= t.day do |day, compromissos| %>
	<%= day.day %>
	<% compromissos.each do |compromisso| %><br>
	<%= link_to h(compromisso.titulo), compromisso %><br>
	<%= link_to 'Editar', edit_compromisso_path(compromisso) %> | <%= link_to 'Deletar', compromisso, method: :delete, data: { confirm: 'Tem certeza?' } %>
	<% end %>
	<% end %>
	<% end %>
</div>
{% endhighlight %}

Adicionar as setas para navegar pelo calendário, app/views/projects/index.html.erb: 

{% highlight erb %}
<div id="calendar">
	<h2 id="month">
		<%= link_to "<", :month => (@date.beginning_of_month-1).strftime("%Y-%m-%d") %>
		<%=h @date.strftime("%B %Y") %>
		<%= link_to ">", :month => (@date.end_of_month+1).strftime("%Y-%m-%d") %>
	</h2>
	<%= calendar_for @compromissos, :year => @date.year, :month => @date.month do |t| %>
	<%= t.head('DOM','SEG', 'TER', 'QUA', 'QUI', 'SEX', 'SAB') %>
	<%= t.day do |day, compromissos| %>
	<%= day.day %>
	<% compromissos.each do |compromisso| %><br>
	<%= link_to h(compromisso.titulo), compromisso %><br>
	<%= link_to 'Editar', edit_compromisso_path(compromisso) %> | <%= link_to 'Deletar', compromisso, method: :delete, data: { confirm: 'Tem certeza?' } %>
	<% end %>
	<% end %>
	<% end %>
</div>
<%= link_to 'Novo Compromisso', new_compromisso_path %>
{% endhighlight %}

Resultado final:
<figure>
	<img src="../assets/img/calendar2.png">
</figure>

<figure>
	<img src="../assets/img/calendar3.png">
</figure>

Código fonte: <a href="https://github.com/alinebone/AgendaDeCompromissos">**Github**</a><br/>
Demo: <a href="http://tutorialagenda.herokuapp.com/compromissos">**Heroku**</a>

Obrigada!
