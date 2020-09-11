---
title: Anatomia pakietu VSIX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33cecb4767193010d7e7ca330d891d1835091875
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012337"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia pakietu VSIX
Pakiet VSIX to plik *. vsix* , który zawiera co najmniej jedno rozszerzenie programu Visual Studio, wraz z metadanymi, które są używane przez program Visual Studio do klasyfikowania i instalowania rozszerzeń. Metadane są zawarte w manifeście VSIX i pliku *[Content_Types]. XML* . Pakiet VSIX może również zawierać co najmniej jeden plik *rozszerzenia. vsixlangpack* , aby zapewnić zlokalizowany tekst instalacji i może zawierać dodatkowe pakiety VSIX, aby zainstalować zależności.

 Format pakietu VSIX jest zgodny ze standardem Open Package Conventions (OPC). Pakiet zawiera dane binarne i pliki pomocnicze wraz z plikiem *[Content_Types]. XML* i plikiem manifestu *. vsix* . Jeden pakiet VSIX może zawierać dane wyjściowe wielu projektów, a nawet wiele pakietów, które mają własne manifesty.

> [!NOTE]
> Nazwy plików zawartych w pakietach VSIX nie mogą zawierać spacji ani znaków, które są zarezerwowane w Uniform Resource Identifier (URI), zgodnie z definicją w obszarze [ \[ RFC2396 \] ](https://www.rfc-editor.org/rfc/rfc2396.txt).

## <a name="the-vsix-manifest"></a>Manifest VSIX
 Manifest VSIX zawiera informacje o rozszerzeniu, które mają zostać zainstalowane, i następuje po schemacie VSX. Aby uzyskać więcej informacji, zobacz [Informacje o schemacie rozszerzenia VSIX 1,0](/previous-versions/dd393700(v=vs.110)). Przykładowy manifest VSIX można znaleźć w temacie [PackageManifest element (root element, VSX Schema)](/previous-versions/dd393754(v=vs.110)).

 Manifest VSIX musi mieć nazwę `extension.vsixmanifest` , gdy jest zawarty w pliku ^. VSIX *.

## <a name="the-content"></a>Zawartość
 Pakiet VSIX może zawierać szablony, elementy przybornika, pakietów VSPackage lub dowolny inny rodzaj rozszerzenia, które jest obsługiwane przez program Visual Studio.

## <a name="language-packs"></a>Pakiety językowe
 Pakiet VSIX może zawierać co najmniej jeden plik *rozszerzenia. vsixlangpack* , aby zapewnić zlokalizowany tekst podczas instalacji. Aby uzyskać więcej informacji, zobacz [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Zależności i odwołania
 Pakiet VSIX może zawierać inne pakiety VSIX jako odwołania. Każdy z tych pakietów musi zawierać swój własny manifest VSIX.

 Jeśli użytkownik spróbuje zainstalować rozszerzenie, które ma zależności, Instalator sprawdzi, czy wymagane zestawy są zainstalowane w systemie użytkownika. Jeśli nie odnaleziono wymaganych zestawów, **rozszerzenia i aktualizacje** będą wyświetlać listę brakujących zestawów.

 Jeśli manifest rozszerzenia zawiera jeden lub więcej elementów [odniesienia](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) , **rozszerzenia i aktualizacje** porównują manifest każdego odwołania do rozszerzeń zainstalowanych w systemie i instalują przywoływane rozszerzenie, jeśli nie jest jeszcze zainstalowane. Jeśli jest zainstalowana wcześniejsza wersja rozszerzenia, jego nowsza wersja zastępuje ją.

 Jeśli projekt w rozwiązaniu obejmującym wiele projektów zawiera odwołanie do innego projektu w tym samym rozwiązaniu, pakiet VSIX zawiera zależności tego projektu. Możesz przesłonić to zachowanie, wybierając odwołanie dla projektu wewnętrznego, a następnie w oknie **Właściwości** Ustaw **grupy wyjściowe zawarte we właściwości VSIX** na `BuiltProjectOutputGroup` .

 Aby uwzględnić satelitarne biblioteki DLL z przywoływanych zestawów w pakiecie VSIX, Dodaj `SatelliteDllsProjectOutputGroup` do **grup wyjściowych zawartych we właściwości VSIX** .

## <a name="installation-location"></a>Miejsce instalacji
 Podczas instalacji **rozszerzenia i aktualizacje** wyszukują zawartość pakietu VSIX w folderze w obszarze *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*.

 Domyślnie instalacja ma zastosowanie tylko do bieżącego użytkownika, ponieważ *% LocalAppData%* jest katalogiem specyficznym dla użytkownika. Jeśli jednak ustawisz element [ALLUSERS](/previous-versions/ee191547(v=vs.110)) manifestu na `True` , rozszerzenie zostanie zainstalowane w obszarze <em>.. \\ </em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> i będzie dostępny dla wszystkich użytkowników komputera.

## <a name="content_typesxml"></a>[Content_Types]. XML
 Plik *[Content_Types]. XML* identyfikuje typy plików w rozwiniętym pliku *VSIX* . Program Visual Studio używa tego pliku podczas instalacji pakietu, ale nie instaluje samego pliku. Aby uzyskać więcej informacji na temat tego pliku, zobacz [strukturę pliku XML [Content_Types]](the-structure-of-the-content-types-dot-xml-file.md).

 Plik *[Content_Types]. XML* jest wymagany przez Standard OPC (Open pakowanie Conventions). Aby uzyskać więcej informacji na temat OPC, zobacz [OPC: A New Standard for pakowanie danych](/archive/blogs/msdnmagazine/opc-a-new-standard-for-packaging-your-data) w witrynie MSDN w sieci Web.