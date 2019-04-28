---
title: Schema Cache | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0ed32908212f158532e5553752ef5c0b70306fe6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435341"
---
# <a name="schema-cache"></a>Pamięć podręczna schematów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor XML udostępnia pamięci podręcznej schematów znajduje się w katalogu %InstallRoot%\Xml\Schemas. Pamięci podręcznej schematu jest globalne dla wszystkich użytkowników na komputerze i zawiera standardowe schematów XML, które są używane do weryfikacji dokumentu IntelliSense i XML.  

 W edytorze XML, można również znaleźć schematów znajduje się w rozwiązaniu, schematy określone w **schematów** pola dokumentu **właściwości** okna i schematy identyfikowane przez `xsi:schemaLocation` i `xsi:noNamespaceSchemaLocation`atrybutów.  

 W poniższej tabeli opisano schematów, które są instalowane za pomocą edytora XML.  

|     Nazwa pliku      |                                                      Opis                                                      |
|-------------------|-----------------------------------------------------------------------------------------------------------------------|
|    Catalog.xsd    |             Schemat dla plików wykazu schematu edytora XML. Informacje o wykazów schematów można znaleźć poniżej.             |
| DotNetConfig.xsd  |                 Schemat dla plików Web.Config "<http://schemas.microsoft.com/.NETConfiguration/v2.0>".                 |
|    msbuild.xsd    |              Schemat dla plików marka MSBuild, "<http://schemas.microsoft.com/developer/msbuild/2003>".              |
|    msdata.xsd     | Schematu dla adnotacji XSD dodane przez <xref:System.Data.DataSet> klasy, "urn: schemas-microsoft-com: XML-msdata". |
|     msxsl.xsd     |                  Schemat rozszerzenia blok skryptu XSLT firmy Microsoft, urn: schemas-microsoft-com:xslt.                   |
| SnippetFormat.xsd |                 Schemat dla plików XML fragmentu kodu. Przykłady można znaleźć w temacie %InstallDir%\VC#\Expansions.                 |
|    Soap1.1.xsd    |            Schemat dla Simple Object Access Protocol (SOAP) 1.1, http://schemas.xmlsoap.org/soap/envelope/.            |
|    Soap1.2.xsd    |                                     Schemat dla Simple Object Access Protocol 1.2.                                     |
| SiteMapSchema.xsd |            Schemat pliku XML mapy witryny ASP.NET "<http://schemas.microsoft.com/AspNet/SiteMap-File-1.0>".             |
|     wsdl.xsd      |                    Schemat dla język opisu usługi sieci Web, http://schemas.xmlsoap.org/wsdl/.                     |
|     xenc.xsd      |                            Schemat XML szyfrowania, http://www.w3.org/2000/09/xmldsig#.                             |
|     xhtml.xsd     |                                    Schemat dla XHTML http://www.w3.org/1999/xhtml.                                     |
|     xlink.xsd     |                                  Schemat dla XLink1.0, http://www.w3.org/1999/xlink.                                   |
|      xml.xsd      |              Schemat opisujący atrybuty XML: Space i XML: lang, http://www.w3.org/XML/1998/namespace.               |
|    xmlsig.xsd     |                        Schemat XML podpisów cyfrowych, http://www.w3.org/2000/09/xmldsig#.                         |
|   xsdschema.xsd   |                            Schemat XSD, opisujący http://www.w3.org/2001/XMLSchema.                            |
|     xslt.xsd      |                           Przekształca schemat dla formatu XML, http://www.w3.org/1999/XSL/Transform.                            |

## <a name="updating-schemas-in-the-cache"></a>Aktualizowanie schematów w pamięci podręcznej  
 Edytor ładuje katalog pamięci podręcznej schematu, gdy pakiet edytora XML jest ładowany i oczekuje na zmiany podczas uruchamiania. Dodano schemat jest automatycznie ładowany do indeksu w pamięci znanych schematów. Jeśli schemat został usunięty, zostanie on automatycznie usunięty z indeksu w pamięci. Jeśli schemat został zaktualizowany, automatycznie unieważnia w pamięci podręcznej tego schematu.  

> [!NOTE]
> Ponieważ katalog pamięci podręcznej schematu jest globalne do komputera, należy dodawać tylko w tym miejscu schematów, które są standardowe i przydatne dla wszystkich projektów programu Visual Studio, które może zostać utworzony na tym komputerze.  

 Edytor XML obsługuje również dowolną liczbę schematu katalogu plików w katalogu pamięci podręcznej schematu. Wykazów schematów można wskazać do innych lokalizacji dla schematów, które mają zawsze edytora, aby dowiedzieć się o. Plik catalog.xsd definiuje format pliku wykazu i znajduje się w katalogu pamięci podręcznej schematu. Plik catalog.xml jest domyślna i zawiera łącza do innych schematów w InstallDir %. Poniżej przedstawiono niektóre spośród pliku catalog.xml:  

```  
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">  
  <Schema href="%InstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>  
  <Schema href="%InstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>  
  <Schema href="%InstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>  
</SchemaCatalog>  
```  

 `href` Atrybut może być dowolnym pliku ścieżki lub http adres URL wskazujący schematu. Ścieżka pliku może być względem dokumentów w katalogu. Następujące zmienne, rozdzielone %%, są rozpoznawane przez Edytor który będzie wdrażany w ścieżce:  

- InstallDir  

- System  

- ProgramFiles  

- Programy  

- CommonProgramFiles  

- ApplicationData  

- CommonApplicationData  

- LCID  

  Dokument wykazu mogą obejmować `Catalog` element, który wskazuje na inne katalogi. Możesz użyć `Catalog` elementu do punktu centralnego katalog udostępniony przez zespół lub firma lub wykaz online udostępnione dla partnerów biznesowych. `href` Atrybut jest plik ścieżki lub http adres URL dla innych katalogów. Oto przykład `Catalog` elementu:  

```  
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>  
```  

 Katalog można także kontrolować, jak schematy są skojarzone z dokumentów XML za pomocą specjalnych `Association` elementu. Ten element kojarzy schematów, które ma docelowego obszaru nazw z konkretnego rozszerzenia pliku, który może być przydatne, ponieważ edytora XML nie wykonuje żadnych skojarzenie automatyczne, schematów, które nie mają `targetNamespace` atrybutu. W poniższym przykładzie `Association` elementu kojarzy schematu dotNetConfig przy użyciu wszystkich plików, które mają rozszerzenie pliku "Konfiguracja":  

```  
<Association extension="config" schema="%InstallDir%/xml/schemas/dotNetConfig.xsd"/>  
```  

## <a name="localized-schemas"></a>Zlokalizowane schematów  
 W wielu przypadkach plik catalog.xml nie zawiera wpisy dla zlokalizowanych schematów. Możesz dodać dodatkowe wpisy do pliku catalog.xml, który wskazywać katalog zlokalizowane schematu.  

 W poniższym przykładzie nowej `Schema` element została utworzona używającej % zmienna % LCID wskaż zlokalizowane schematu.  

```  
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"  
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>  
```  

## <a name="changing-the-location-of-the-schema-cache"></a>Zmienianie lokalizacji pamięci podręcznej schematów  
 Można dostosować lokalizację przy użyciu pamięci podręcznej schematu **różne** Strona opcji. W przypadku katalogu schematów ulubionego edytora można skonfigurować do zamiast tego użyj tych schematów.  

> [!NOTE]
> Ta zmiana dotyczy tylko bieżącego użytkownika programu Visual Studio.  

#### <a name="to-change-the-schema-cache-location"></a>Aby zmienić lokalizację pamięci podręcznej schematu  

1. Z **narzędzia** menu, wybierz opcję **opcje**.  

2. Rozwiń **edytora tekstów**, rozwiń węzeł **XML**, a następnie kliknij przycisk **różne**.  

3. Kliknij przycisk **Przeglądaj** znajdujący się na **schematów** pola.  

4. Wybierz folder dla pamięci podręcznej schematu, a następnie kliknij przycisk **OK**.  

#### <a name="to-add-another-directory-of-common-schemas"></a>Aby dodać inny katalog typowych schematów  

1. Edytuj plik catalog.xml w katalogu pamięci podręcznej schematu edytora XML.  

2. Dodaj nową `<Catalog href="…"/>` element, który wskazuje katalog dodatkowe schematów.  

3. Zapisz zmiany.  

     Katalog jest automatycznie ponownie ładowane.  

## <a name="see-also"></a>Zobacz też  
 [Edytor XML](../xml-tools/xml-editor.md)
