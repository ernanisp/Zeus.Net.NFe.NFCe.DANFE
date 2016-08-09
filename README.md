# Zeus.Net.NFe.NFCe.DANFE

Biblioteca gratuita para visualizar/imprimir e exportar para PDF e outros formatos, o DANFE da NFCe, conforme regulamentados nos manuais disponíveis em http://www.nfe.fazenda.gov.br/portal/principal.aspx

A biblioteca foi desenvolvida com o Visual Studio Community 2015, update 3, mas é compatível com o Visual Studio Community 2013. Está licenciada sobre a LGPL.

Esta biblioteca utiliza o FastReports.NET para impressão.
Uma versão demo do FastReport pode ser baixada em https://www.fast-report.com/pt/product/fast-report-net/

Instruções para compilar a solução

No visual studio, abra o arquivo "Zeus.Net.NFe.NFCe.DANFE.sln", defina o "NFe.AppTeste" como projeto de inicialização, compile e execute.
Projetos na Solução

NFe.Danfe.AppTeste: Aplicação em wpf com demonstração de uso da biblioteca;
NFe.Danfe.Fast: Biblioteca responsável por montar a impressão do DANFE.

**TODO:**
- [x] Implementar impressão do DANFE de NFCe Mini. Concluído em 09/09/2015;
- [ ] Implementar impressão do DANFE de NFCe A4;
- [ ] Implementar impressão do DANFE de NFe;
- [ ] Implementar possíveis mudanças no Manual de Padrões Padrões Técnicos do DANFE-NFC-e e QR Code, versão 3.3 que será obrigatório a
 partir de  01/09/2016;
- [ ] Alterações no DANFE de NFCe (Adicionar opção para definir o tamanho da logomarca);
- [x] Adicionar opção para determinar se o desconto por item deve ser impresso.



**DANFE**
- Foi implementado em 09/09/2015 a impressão do NFCe em Fast Reports (https://www.fast-report.com/pt/product/fast-report-net/);
- Os recursos implementados na biblioteca de impressão foram: Visualização e impressão direta, além dos recursos de exportação para pdf, xls, doc, etc. do próprio Fast Reports;
- A impressão segue rigorosamente o Manual de Especificacoes Tecnicas do DANFE NFC-e QRCode Versao 3.2);
- Obs: Visando abranger o maior número possível de impressoras térmicas, a impressão é feita via spooler do windows. A impressão térmica via spooler, dependendo da impressora, pode sair com má qualidade. Para sanar isso, no relatório são utlizadas duas fontes condensadas que possuem boa legibilidade em tamanho pequeno, a saber a OpenSans e UbuntuCondensed, ambas de uso livre podendo ser obtidas em https://www.google.com/fonts;
- As fontes estão anexadas ao projeto em NFe.Impressao\NFCe\Fontes;
- Instale as fontes informadas no PC que for imprimir o DANFE da NFCe;
- Impressão testada e funcionando 100% nas impressoras Bematech MP-4200, Daruma DR700 e Epson TM-81 e TM-20.

Exemplo de impressão do DANFE da NFCe utilizando a bilbioteca:

```cs
var proc = new nfeProc().CarregarDeArquivoXml(Caminho_do_arquivo_XML);
var danfe = new DanfeFrNfce(proc, new ConfiguracaoDanfeNfce(NfceDetalheVendaNormal.UmaLinha, NfceDetalheVendaContigencia.UmaLinha, null/*Logomarca em byte[]*/), "00001", "XXXXXXXXXXXXXXXXXXXXXXXXXX");
danfe.Visualizar();
//danfe.Imprimir();
//danfe.ExibirDesign();

```
![](http://www.zeusautomacao.com.br/imagens/git/07.png)

