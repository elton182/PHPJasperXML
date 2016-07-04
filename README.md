#PHPJasperXML

*Criei esse pacote com a inteção de atualizar e utilizar essa biblioteca que facilita a criação de relatórios atravez o IReport, o maior report designer open source do mercado.

Foi utilizado a ulitma versão do PHPJasperXML que encontrei na web ("http://www.simitgroup.com/?q=PHPJasperXML") versão: 9d.

Atualizei as classes com namespaces para poder usar atravez da PSR-4 (autoload).



##Como Usar:

1. Baixe e coloque no diretório vendor do seu projeto, na seguinte estrutura *vendor/PHPJasperXML/PHPJasperXML/src*
2. Coloque no seu composer.json na area psr-4: *"PHPJasperXML\\": "./vendor/PHPJasperXML/PHPJasperXML/src"*
3. Rode o composer dump-autoload
4. No controller que for usar coloque:

	```php
	use Cake\Datasource\ConnectionManager;
	use PHPJasperXML\TCPDF;
	use PHPJasperXML\PHPJasperXML;

 	$PHPJasperXML = new PHPJasperXML();
    $PHPJasperXML->PHPJasperXML();

    $PHPJasperXML->arrayParameter=array("parameter1"=>'');
    $PHPJasperXML->load_xml_file( ROOT . DS . APP_DIR .  "\\Reports\\OccurrenceDetail.jrxml");

    $con = ConnectionManager::config('default');
    $PHPJasperXML->transferDBtoArray($con['host'],$con['username'],$con['password'],$con['database']);
    $PHPJasperXML->outpage("I");    //page output method I:standard output  D:Download file


    ```

