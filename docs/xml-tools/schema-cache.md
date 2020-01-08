---
title: Pamięć podręczna schematu edytora XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40781a5249d9b69df5f41f863f3d36ac6a119645
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592493"
---
# <a name="schema-cache"></a>Pamięć podręczna schematów

Edytor XML udostępnia pamięć podręczną schematu znajdującą się w katalogu *%VSInstallDir%\xml\Schemas* . Pamięć podręczna schematu jest globalna dla wszystkich użytkowników na komputerze i zawiera standardowe schematy XML, które są używane do sprawdzania poprawności dokumentów IntelliSense i XML.

Edytor XML może również znajdować schematy znajdujące się w rozwiązaniu, schematy określone w polu **schematy** okna **Właściwości** dokumentu i schematy identyfikowane przez atrybuty `xsi:schemaLocation` i `xsi:noNamespaceSchemaLocation`.

W poniższej tabeli opisano schematy, które są instalowane z edytorem XML.

| Nazwa pliku | Opis |
|-| - |
| *catalog.xsd* | Schemat dla plików wykazu schematu edytora XML. Aby uzyskać informacje na temat wykazów schematu, zobacz poniżej. |
| *DotNetConfig.xsd* | Schemat dla plików Web. config, `http://schemas.microsoft.com/.NETConfiguration/v2.0`. |
| *msbuild.xsd* | Schemat programu MSBuild Make plików `http://schemas.microsoft.com/developer/msbuild/2003`. |
| *msdata.xsd* | Schemat adnotacji XSD dodanych przez klasę <xref:System.Data.DataSet> "urn: schematys-Microsoft-com: XML-msdata". |
| *msxsl.xsd* | Schemat dla rozszerzeń bloku skryptu Microsoft XSLT, urn: schematy — Microsoft-com: XSLT. |
| *SnippetFormat.xsd* | Schemat dla plików XML fragmentów kodu. Aby zapoznać się z przykładami, zobacz *% VSInstallDir%VC#\ \Expansions*. |
| *SOAP 1.1. xsd* | Schemat dla Simple Object Access Protocol (SOAP) 1,1, `http://schemas.xmlsoap.org/soap/envelope/`. |
| *SOAP 1.2. xsd* | Schemat dla Simple Object Access Protocol 1,2. |
| *SiteMapSchema.xsd* | Schemat dla pliku XML mapy ASP.NET Sitemap, `http://schemas.microsoft.com/AspNet/SiteMap-File-1.0`. |
| *wsdl.xsd* | Schemat opisu usługi sieci Web, `http://schemas.xmlsoap.org/wsdl/`. |
| *xenc. xsd* | Schemat szyfrowania XML, `http://www.w3.org/2000/09/xmldsig#`. |
| *xhtml.xsd* | Schemat dla `http://www.w3.org/1999/xhtml`XHTML. |
| *xlink.xsd* | Schemat dla XLink 1.0, `http://www.w3.org/1999/xlink`. |
| *xml.xsd* | Schemat opisujący atrybuty XML: Space i XML: lang, `http://www.w3.org/XML/1998/namespace`. |
| *xmlsig.xsd* | Schemat dla podpisów cyfrowych XML, `http://www.w3.org/2000/09/xmldsig#`. |
| *xsdschema.xsd* | Schemat opisujący sam XSD, `http://www.w3.org/2001/XMLSchema`. |
| *xslt.xsd* | Schemat transformacje XML, `http://www.w3.org/1999/XSL/Transform`. |

## <a name="update-schemas-in-the-cache"></a>Aktualizowanie schematów w pamięci podręcznej

Edytor ładuje Katalog pamięci podręcznej schematu, gdy pakiet edytora XML jest ładowany i obserwuje zmiany podczas uruchamiania. Jeśli schemat został dodany, zostanie automatycznie załadowany do indeksu znajdującego się w pamięci znanych schematów. Jeśli schemat został usunięty, zostanie automatycznie usunięty z indeksu znajdującego się w pamięci. Jeśli schemat został zaktualizowany, automatycznie unieważnia pamięć podręczną w pamięci w tym schemacie.

> [!NOTE]
> Ponieważ katalog pamięci podręcznej schematu jest globalny dla komputera, należy dodać tylko schematy, które są standardowe i przydatne dla wszystkich projektów programu Visual Studio, które mogą być tworzone na komputerze.

Edytor XML obsługuje również dowolną liczbę plików wykazu schematu w katalogu pamięci podręcznej schematu. Wykazy schematu mogą wskazywać inne lokalizacje dla schematów, które zawsze mają być znane przez Edytor. Plik *Catalog. xsd* definiuje format pliku wykazu i znajduje się w katalogu pamięci podręcznej schematu. Plik *Catalog. XML* jest katalogiem domyślnym i zawiera linki do innych schematów w *% VSInstallDir%* . Poniżej znajduje się próbkowanie pliku *Catalog. XML* :

```xml
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%VSInstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

Atrybutem `href` może być dowolna ścieżka pliku lub adres URL http wskazujący schemat. Ścieżka pliku może być względna dla dokumentu wykazu. Następujące zmienne, rozdzielane przez%%, są rozpoznawane przez Edytor i rozwinięte w ścieżce:

- VSInstallDir

- System

- ProgramFiles

- Programy

- CommonProgramFiles

- ApplicationData

- CommonApplicationData

- LCID

Dokument wykazu może zawierać element `Catalog`, który wskazuje na inne wykazy. Można użyć elementu `Catalog`, aby wskazać centralny katalog współużytkowany przez zespół lub firmę lub katalog online udostępniony partnerom biznesowym. Atrybut `href` jest ścieżką pliku lub adresem URL protokołu HTTP dla innych wykazów. Poniżej przedstawiono przykład elementu `Catalog`:

```xml
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

Wykaz może również kontrolować sposób, w jaki schematy są skojarzone z dokumentami XML przy użyciu specjalnego elementu `Association`. Ten element kojarzy schematy, które nie mają docelowej przestrzeni nazw z określonym rozszerzeniem pliku, co może być przydatne, ponieważ Edytor XML nie wykonuje żadnych autoskojarzenia schematów, które nie mają atrybutu `targetNamespace`. W poniższym przykładzie element `Association` kojarzy schemat żaden plik DotNetConfig ze wszystkimi plikami, które mają rozszerzenie pliku "config":

```xml
<Association extension="config" schema="%VSInstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>Zlokalizowane schematy

W wielu przypadkach plik *Catalog. XML* nie zawiera wpisów dla zlokalizowanych schematów. Do pliku *Catalog. XML* można dodać dodatkowe wpisy wskazujące zlokalizowany katalog schematu.

W poniższym przykładzie został utworzony nowy element `Schema`, który używa zmiennej% LCID%, aby wskazać zlokalizowany schemat.

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="change-the-location-of-the-schema-cache"></a>Zmiana lokalizacji pamięci podręcznej schematu

Lokalizację pamięci podręcznej schematu można dostosować za pomocą strony **różne** opcje. Jeśli masz katalog ulubionych schematów, Edytor można skonfigurować tak, aby korzystał z tych schematów.

> [!NOTE]
> Ta zmiana ma wpływ tylko na bieżącego użytkownika programu Visual Studio.

### <a name="to-change-the-schema-cache-location"></a>Aby zmienić lokalizację pamięci podręcznej schematu

1. W menu **Narzędzia** wybierz pozycję **Opcje**.

2. Rozwiń węzeł **Edytor tekstu**, rozwiń pozycję **XML**, a następnie kliknij pozycję **różne**.

3. Kliknij przycisk **Przeglądaj** w polu **schematy** .

4. Wybierz folder dla pamięci podręcznej schematu, a następnie kliknij przycisk **OK**.

### <a name="to-add-another-directory-of-common-schemas"></a>Aby dodać inny katalog dla wspólnych schematów

1. Edytuj plik *Catalog. XML* w katalogu pamięci podręcznej schematu edytora XML.

2. Dodaj nowy element `<Catalog href="..."/>`, który wskazuje katalog dodatkowych schematów.

3. Zapisz zmiany.

   Wykaz zostanie automatycznie załadowany ponownie.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)
