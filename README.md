# BDD
use agenda;
-- select * from telefone;

-- listar todos os contatos cadastrados e seus respectivos telefones (mesmo que não tenha telefone cadastrado)
select c.nome, t.numero, t.tipofone from contato as c left join telefone as t on c.idcontato = t.idcontato;

--  Mostrar todas as localizações de compromissos e os contatos que participarão, incluindo locais sem participantes:
select comp.localizacao, comp.descricao, c.nome from compromisso as comp left join contato_compromisso as cc on comp.idcompromisso = cc.idcompromisso left join 
contato as c on cc.idcontato = c.idcontato;

-- Exibir todos os telefones cadastrados, mostrando o tipo do telefone, tempo médio de ligação e nome do contato associado (se houver):
select t.tipofone, t.tempoligacao, c.nome from contato as c right join telefone as t on c.idcontato = t.idcontato order by t.tipofone asc;

-- Listar todos os compromissos e, quando houver, exibir o nome e a cidade dos contatos participantes:
select comp.descricao, comp.localizacao, c.nome, c.cidade from contato as c right join contato_compromisso as cc on c.idcontato = cc.idcontato right join compromisso
as comp on cc.idcompromisso = comp.idcompromisso order by comp.data asc;

-- extrair o ddd, nome dos cadastros em banco junto dos seus respectivos estados bem como as datas dos eventos que cada participante vai comparecer:
select t.ddd, c.nome, c.uf, comp.data from telefone as t left join contato as c on c.idcontato = t.idcontato left join contato_compromisso as cc on
c.idcontato = cc.idcontato left join compromisso as comp on comp.idcompromisso = cc.idcompromisso;

-- 
select c.nome, t.numero, t.tipofone from contato as c left join telefone as t on c.idcontato = t.idcontato union
select c.nome, t.numero, t.tipofone from contato as c right join telefone as t on c.idcontato = t.idcontato;
