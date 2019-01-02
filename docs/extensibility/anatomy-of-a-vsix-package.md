---
title: Anatomia pakietu VSIX | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9fa23b603f8eb94ebca5256145b7fb7df837d40
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921487"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia pakietu VSIX
Pakiet VSIX jest *.vsix* pliku, który zawiera jeden lub więcej rozszerzeń programu Visual Studio, razem z metadanymi programu Visual Studio używa do klasyfikowania i zainstalować rozszerzenia. Tych metadanych znajduje się w manifestu VSIX i *[Content_Types] .xml* pliku. Pakiet VSIX może również zawierać co najmniej jeden *Extension.vsixlangpack* plików w celu zapewnienia zlokalizowane w tekście Instalatora i może zawierać dodatkowe pakiety VSIX, aby zainstalować zależności.  
  
 Formacie pakietu VSIX postępuje zgodnie ze standardowym otwarte konwencje tworzenia pakietów (OPC). Pakiet zawiera pliki binarne i pliki pomocnicze, wraz z *[Content_Types] .xml* pliku i *.vsix* pliku manifestu. Jeden pakiet VSIX może zawierać dane wyjściowe z wieloma projektami lub nawet utworzyć wiele pakietów, które mają własne manifestów.  
  
> [!NOTE]
>  Nazwy plików zawarte w pakietów VSIX nie może zawierać spacji ani znaków, które są zastrzeżone w identyfikatorach URI (Uniform Resource), zdefiniowane w obszarze [ \[specyfikacja RFC 2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>VSIX manifest  
 VSIX manifest zawiera informacje dotyczące rozszerzenia do zainstalowania, a schemat VSX w następujący sposób. Aby uzyskać więcej informacji, zobacz [odwołanie do schematu 1.0 rozszerzenia VSIX](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Aby uzyskać przykład manifestu VSIX, zobacz [PackageManifest elementu (element główny, schemat VSX)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 VSIX manifest, musi nosić `extension.vsixmanifest` gdy wchodzi on w ^ pliku .vsix *.  
  
## <a name="the-content"></a>Zawartość  
 Pakiet VSIX może zawierać szablony, elementy do przybornika, pakietów VSPackage lub dowolny inny rodzaj rozszerzenia, która jest obsługiwana przez program Visual Studio.  
  
## <a name="language-packs"></a>Pakiety językowe  
 Pakiet VSIX może zawierać jeden raz lub więcej *Extension.vsixlangpack* plików, aby zapewnić zlokalizowanego tekstu podczas instalacji. Aby uzyskać więcej informacji, zobacz [pakietów VSIX lokalizowanie](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Zależności i odwołań  
 Pakiet VSIX może zawierać innych pakietów VSIX jako odwołania. Każda z tych innych pakietów musi zawierać VSIX manifest.  
  
 Jeśli użytkownik próbuje zainstalować rozszerzenie, które ma zależności, Instalator sprawdza, czy wymagane zestawy są zainstalowane w systemie użytkownika. Jeśli nie ma wymaganych zestawów, **rozszerzenia i aktualizacje** Wyświetla listę brakujących zestawów.  
  
 Jeśli manifest rozszerzenia zawiera co najmniej jedną [odwołania](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) elementów **rozszerzenia i aktualizacje** porównuje manifest każde odwołanie do rozszerzenia, które są zainstalowane w systemie, a następnie instaluje Odwołanie do rozszerzenia, jeśli nie jest już zainstalowany. Jeśli jest zainstalowana wcześniejsza wersja odwołania rozszerzenia, nowsza wersja zastępuje go.  
  
 Jeśli projektu w rozwiązaniu wieloprojektowego zawiera odwołanie do innego projektu w tym samym rozwiązaniu, pakiet VSIX zawiera zależności projektu. Zachowanie to można zastąpić, klikając odwołanie do wewnętrznego projekcie, a następnie w **właściwości** okna, ustawienie **dane wyjściowe grupy uwzględnione w VSIX** właściwość `BuiltProjectOutputGroup`.  
  
 Aby dołączyć satelickich bibliotek DLL z przywoływanych zestawów w pakiecie VSIX, należy dodać `SatelliteDllsProjectOutputGroup` do **dane wyjściowe grupy uwzględnione w VSIX** właściwości.  
  
## <a name="installation-location"></a>Lokalizacja instalacji  
 Podczas instalacji **rozszerzenia i aktualizacje** szuka zawartości pakietu VSIX w folderze w *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*.  
  
 Domyślnie instalacja ma zastosowanie tylko do bieżącego użytkownika, ponieważ *% LocalAppData %* jest katalogiem specyficzne dla użytkownika. Jednak jeśli ustawisz [AllUsers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) elementu manifestu do `True`, będzie można zainstalować rozszerzenia w ramach <em>... \\</em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> i będzie dostępna dla wszystkich użytkowników komputera.  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 *[Content_Types] .xml* pliku Określa typy plików w rozwiniętym okienku *.vsix* pliku. Visual Studio używa tego pliku podczas instalacji pakietu, ale nie można zainstalować w samym pliku. Aby uzyskać więcej informacji na temat tego pliku, zobacz [struktura pliku [Content_types] .xml](the-structure-of-the-content-types-dot-xml-file.md).  
  
 A *[Content_Types] .xml* plików jest wymagane przez standard Open konwencje tworzenia pakietów (OPC). Aby uzyskać więcej informacji na temat OPC zobacz [OPC: Nowy standard do pakowania danych](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) w witrynie MSDN w sieci Web.