---
title: Anatomia pakietu VSIX | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 8a6d3f994c531bd36ab4281c5f0b27e993cd3392
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740094"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia pakietu VSIX
Pakiet VSIX to plik *vsix,* który zawiera co najmniej jedno rozszerzenie programu Visual Studio, wraz z metadanymi używanymi przez program Visual Studio do klasyfikowania i instalowania rozszerzeń. Te metadane są zawarte w manifeście VSIX i *[Content_Types].xml* pliku. Pakiet VSIX może również zawierać jeden lub więcej plików *Extension.vsixlangpack* w celu zapewnienia zlokalizowanego tekstu konfiguracji i może zawierać dodatkowe pakiety VSIX w celu zainstalowania zależności.

 Format pakietu VSIX jest zgodny ze standardem Open Packaging Conventions (OPC). Pakiet zawiera pliki binarne i pliki pomocnicze, wraz z *plikiem [Content_Types].xml* i plikiem manifestu *.vsix.* Jeden pakiet VSIX może zawierać dane wyjściowe wielu projektów lub nawet wiele pakietów, które mają własne manifesty.

> [!NOTE]
> Nazwy plików zawartych w pakietach VSIX nie mogą zawierać spacji ani znaków zarezerwowanych w jednolitych identyfikatorach zasobów (URI), zgodnie z definicją w obszarze [ \[RFC2396\]](https://www.rfc-editor.org/rfc/rfc2396.txt).

## <a name="the-vsix-manifest"></a>Manifest VSIX
 Manifest VSIX zawiera informacje o rozszerzeniu, które ma zostać zainstalowane, i jest zgodny ze schematem VSX. Aby uzyskać więcej informacji, zobacz [odwołanie do schematu rozszerzenia VSIX 1.0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Na przykład manifest VSIX zobacz [Element PackageManifest (element główny, schemat VSX)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).

 Manifest VSIX musi `extension.vsixmanifest` mieć nazwę, gdy znajduje się w pliku ^.vsix*.

## <a name="the-content"></a>Zawartość
 Pakiet VSIX może zawierać szablony, elementy przybornika, pakiety VSPackages lub innego rodzaju rozszerzenia, które jest obsługiwane przez program Visual Studio.

## <a name="language-packs"></a>Pakiety językowe
 Pakiet VSIX może zawierać raz lub więcej plików *Extension.vsixlangpack,* aby zapewnić zlokalizowany tekst podczas instalacji. Aby uzyskać więcej informacji, zobacz [Lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Zależności i odwołania
 Pakiet VSIX może zawierać inne pakiety VSIX jako odwołania. Każdy z tych innych pakietów musi zawierać własny manifest VSIX.

 Jeśli użytkownik próbuje zainstalować rozszerzenie, które ma zależności, instalator sprawdza, czy wymagane zestawy są zainstalowane w systemie użytkownika. Jeśli nie zostaną znalezione wymagane zestawy, **rozszerzenia i aktualizacje** wyświetli listę brakujących zestawów.

 Jeśli manifest rozszerzenia zawiera jeden lub więcej elementów [odwołania,](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) **rozszerzenia i aktualizacje** porównuje manifest każdego odwołania do rozszerzeń, które są zainstalowane w systemie i instaluje rozszerzenie, do którego istnieje odwołanie, jeśli nie jest jeszcze zainstalowany. Jeśli zostanie zainstalowana wcześniejsza wersja rozszerzenia, do którego istnieje odwołanie, zastąpi ją nowsza wersja.

 Jeśli projekt w rozwiązaniu wielu projektów zawiera odwołanie do innego projektu w tym samym rozwiązaniu, pakiet VSIX zawiera zależności tego projektu. To zachowanie można zastąpić, klikając odwołanie do projektu wewnętrznego, a następnie w oknie **Właściwości** ustawienie właściwości Grupy `BuiltProjectOutputGroup` **wyjściowe zawarte w programie VSIX** na .

 Aby uwzględnić biblioteki DLL satelitarne z zestawów, do których istnieją odwołania, w pakiecie VSIX należy dodać `SatelliteDllsProjectOutputGroup` do grupy **wyjściowe zawarte w vsix** właściwości.

## <a name="installation-location"></a>Miejsce instalacji
 Podczas instalacji **rozszerzenia i aktualizacje wyszukują** zawartość pakietu VSIX w folderze w obszarze *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*.

 Domyślnie instalacja dotyczy tylko bieżącego użytkownika, ponieważ *%LocalAppData%* jest katalogiem specyficznym dla użytkownika. Jeśli jednak ustawisz [allusers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) element `True`manifestu do , rozszerzenie zostanie zainstalowany w <em>obszarze .. \\ </em>VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> i będzie dostępny dla wszystkich użytkowników komputera.

## <a name="content_typesxml"></a>[Content_Types].xml
 *[Content_Types]xml* plik identyfikuje typy plików w rozwiniętym pliku *vsix.* Program Visual Studio używa tego pliku podczas instalacji pakietu, ale nie instaluje samego pliku. Aby uzyskać więcej informacji na temat tego pliku, zobacz [Struktura pliku [Content_types].xml](the-structure-of-the-content-types-dot-xml-file.md).

 Plik *[Content_Types].xml* jest wymagany przez standard Open Packaging Conventions (OPC). Aby uzyskać więcej informacji na temat OPC, zobacz [OPC: Nowy standard pakowania danych](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) w witrynie sieci Web MSDN.
