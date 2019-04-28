---
title: Anatomia pakietu VSIX | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 68ed49b2b22a8302fad0355dde3f937f6b67794b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443935"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia pakietu VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakiet VSIX jest plik .vsix, który zawiera jeden lub więcej rozszerzeń programu Visual Studio, razem z metadanymi używanych przez program Visual Studio do klasyfikowania i zainstalować rozszerzenia. Metadane są zawarte w manifestu VSIX i pliku [Content_Types] .xml. Pakiet VSIX może również zawierać jeden lub więcej plików Extension.vsixlangpack w celu zapewnienia tekście Instalatora zlokalizowanych i może zawierać dodatkowe pakiety VSIX, aby zainstalować zależności.  
  
 Formacie pakietu VSIX postępuje zgodnie ze standardowym otwarte konwencje tworzenia pakietów (OPC). Pakiet zawiera pliki binarne i pliki pomocnicze, wraz z pliku [Content_Types] .xml i plikiem typu .vsix pliku manifestu. Jeden pakiet VSIX może zawierać dane wyjściowe z wieloma projektami lub nawet utworzyć wiele pakietów, które mają własne manifestów.  
  
> [!NOTE]
> Nazwy plików zawarte w pakietów VSIX nie może zawierać spacji ani znaków, które są zastrzeżone w identyfikatorach URI (Uniform Resource), zdefiniowane w obszarze [ \[specyfikacja RFC 2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>VSIX Manifest  
 VSIX manifest zawiera informacje dotyczące rozszerzenia do zainstalowania, a schemat VSX w następujący sposób. Aby uzyskać więcej informacji, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Aby uzyskać przykład manifestu VSIX, zobacz [PackageManifest elementu (Element główny, schemat VSX)](http://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 VSIX manifest, musi nosić `extension.vsixmanifest` gdy wchodzi on w pliku .vsix.  
  
## <a name="the-content"></a>Zawartość  
 Pakiet VSIX może zawierać szablony, elementy do przybornika, pakietów VSPackage lub dowolny inny rodzaj rozszerzenia, która jest obsługiwana przez program Visual Studio.  
  
## <a name="language-packs"></a>Pakiety językowe  
 Pakiet VSIX może zawierać jeden raz lub więcej plików Extension.vsixlangpack zapewnienie zlokalizowanego tekstu podczas instalacji. Aby uzyskać więcej informacji, zobacz [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Zależności i odwołań  
 Pakiet VSIX może zawierać innych pakietów VSIX jako odwołania. Każda z tych innych pakietów musi zawierać VSIX manifest.  
  
 Jeśli użytkownik próbuje zainstalować rozszerzenie, które ma zależności, Instalator sprawdza, czy wymagane zestawy są zainstalowane w systemie użytkownika. Jeśli nie ma wymaganych zestawów, **rozszerzenia i aktualizacje** Wyświetla listę brakujących zestawów.  
  
 Jeśli manifest rozszerzenia zawiera co najmniej jedną [odwołania](http://msdn.microsoft.com/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) elementów **rozszerzenia i aktualizacje** porównuje manifest każde odwołanie do rozszerzenia, które są zainstalowane w systemie, a następnie instaluje Odwołanie do rozszerzenia, jeśli nie jest już zainstalowany. Jeśli jest zainstalowana wcześniejsza wersja odwołania rozszerzenia, nowsza wersja zastępuje go.  
  
 Jeśli projektu w rozwiązaniu wieloprojektowego zawiera odwołanie do innego projektu w tym samym rozwiązaniu, pakiet VSIX zawiera zależności projektu. Zachowanie to można zastąpić, klikając odwołanie do wewnętrznego projekcie, a następnie w **właściwości** okna, ustawienie **dane wyjściowe grupy uwzględnione w VSIX** właściwość `BuiltProjectOutputGroup`.  
  
 Aby dołączyć satelickich bibliotek DLL z przywoływanych zestawów w pakiecie VSIX, należy dodać `SatelliteDllsProjectOutputGroup` do **dane wyjściowe grupy uwzględnione w VSIX** właściwości.  
  
## <a name="installation-location"></a>Lokalizacja instalacji  
 Podczas instalacji **rozszerzenia i aktualizacje** szuka zawartości pakietu VSIX w folderze % LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 Domyślnie instalacja dotyczy tylko bieżącego użytkownika, ponieważ % LocalAppData % to katalog dla określonego użytkownika. Jednak jeśli ustawisz [AllUsers](http://msdn.microsoft.com/ac817f50-3276-4ddb-b467-8bbb1432455b) elementu manifestu do `True`, będzie można zainstalować rozszerzenia w obszarze... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions i będzie dostępna dla wszystkich użytkowników komputera.  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 Pliku [Content_Types] .xml określa typy plików w pliku .vsix rozwinięty. Visual Studio używa tego pliku podczas instalacji pakietu, ale nie można zainstalować w samym pliku. Aby uzyskać więcej informacji na temat tego pliku, zobacz [struktury Content_types\]XML pliku](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
 Pliku [Content_Types] .xml jest wymagana przez otwarty pakowania konwencje pakietów (OPC) standardowa. Aby uzyskać więcej informacji na temat OPC zobacz [OPC: Nowy Standard dla pakowania własnych danych](http://go.microsoft.com/fwlink/?LinkID=148207) w witrynie MSDN w sieci Web.
