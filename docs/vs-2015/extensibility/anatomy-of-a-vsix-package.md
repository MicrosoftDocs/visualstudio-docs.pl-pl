---
title: Anatomia pakietu VSIX | Microsoft Docs
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
ms.openlocfilehash: 156b221265b4c3c23b795b09b9a50ccb27a63bcf
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295649"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia pakietu VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakiet VSIX to plik. vsix, który zawiera co najmniej jedno rozszerzenie programu Visual Studio, wraz z metadanymi, które są używane przez program Visual Studio do klasyfikowania i instalowania rozszerzeń. Metadane są zawarte w manifeście VSIX i pliku [Content_Types]. XML. Pakiet VSIX może również zawierać co najmniej jeden plik rozszerzenia. vsixlangpack, aby zapewnić zlokalizowany tekst instalacji i może zawierać dodatkowe pakiety VSIX, aby zainstalować zależności.  
  
 Format pakietu VSIX jest zgodny ze standardem Open Package Conventions (OPC). Pakiet zawiera dane binarne i pliki pomocnicze wraz z plikiem [Content_Types]. XML i plikiem manifestu. VSIX. Jeden pakiet VSIX może zawierać dane wyjściowe wielu projektów, a nawet wiele pakietów, które mają własne manifesty.  
  
> [!NOTE]
> Nazwy plików zawartych w pakietach VSIX nie mogą zawierać spacji ani znaków, które są zarezerwowane w Uniform Resource Identifier (URI), zgodnie z definicją w obszarze [\[RFC2396\]](https://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>Manifest VSIX  
 Manifest VSIX zawiera informacje o rozszerzeniu, które mają zostać zainstalowane, i następuje po schemacie VSX. Aby uzyskać więcej informacji, zobacz [Informacje o schemacie rozszerzenia VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Przykładowy manifest VSIX można znaleźć w temacie [PackageManifest element (root element, VSX Schema)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 Manifest VSIX musi mieć nazwę `extension.vsixmanifest`, gdy jest zawarty w pliku. VSIX.  
  
## <a name="the-content"></a>Zawartość  
 Pakiet VSIX może zawierać szablony, elementy przybornika, pakietów VSPackage lub dowolny inny rodzaj rozszerzenia, które jest obsługiwane przez program Visual Studio.  
  
## <a name="language-packs"></a>Pakiety językowe  
 Pakiet VSIX może zawierać co najmniej jeden plik rozszerzenia. vsixlangpack, aby zapewnić zlokalizowany tekst podczas instalacji. Aby uzyskać więcej informacji, zobacz [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Zależności i odwołania  
 Pakiet VSIX może zawierać inne pakiety VSIX jako odwołania. Każdy z tych pakietów musi zawierać swój własny manifest VSIX.  
  
 Jeśli użytkownik spróbuje zainstalować rozszerzenie, które ma zależności, Instalator sprawdzi, czy wymagane zestawy są zainstalowane w systemie użytkownika. Jeśli nie odnaleziono wymaganych zestawów, **rozszerzenia i aktualizacje** będą wyświetlać listę brakujących zestawów.  
  
 Jeśli manifest rozszerzenia zawiera jeden lub więcej elementów [odniesienia](https://msdn.microsoft.com/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) , **rozszerzenia i aktualizacje** porównują manifest każdego odwołania do rozszerzeń zainstalowanych w systemie i instalują przywoływane rozszerzenie, jeśli nie jest jeszcze zainstalowane. Jeśli jest zainstalowana wcześniejsza wersja rozszerzenia, jego nowsza wersja zastępuje ją.  
  
 Jeśli projekt w rozwiązaniu obejmującym wiele projektów zawiera odwołanie do innego projektu w tym samym rozwiązaniu, pakiet VSIX zawiera zależności tego projektu. Możesz przesłonić to zachowanie, klikając odwołanie do projektu wewnętrznego, a następnie w oknie **Właściwości** , ustawiając **grupy wyjściowe zawarte we właściwości VSIX** do `BuiltProjectOutputGroup`.  
  
 Aby uwzględnić satelitarne biblioteki DLL z przywoływanych zestawów w pakiecie VSIX, Dodaj `SatelliteDllsProjectOutputGroup` do **grup wyjściowych zawartych we właściwości VSIX** .  
  
## <a name="installation-location"></a>Miejsce instalacji  
 Podczas instalacji **rozszerzenia i aktualizacje** wyszukują zawartość pakietu VSIX w folderze w obszarze%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 Domyślnie instalacja ma zastosowanie tylko do bieżącego użytkownika, ponieważ% LocalAppData% jest katalogiem specyficznym dla użytkownika. Jeśli jednak ustawisz element [ALLUSERS](https://msdn.microsoft.com/ac817f50-3276-4ddb-b467-8bbb1432455b) manifestu na `True`, rozszerzenie zostanie zainstalowane w obszarze..\\*VisualStudioInstallationFolder*\Common7\IDE\Extensions i będzie dostępny dla wszystkich użytkowników komputera.  
  
## <a name="content_typesxml"></a>[Content_Types]. XML  
 Plik [Content_Types]. XML identyfikuje typy plików w rozwiniętym pliku VSIX. Program Visual Studio używa tego pliku podczas instalacji pakietu, ale nie instaluje samego pliku. Aby uzyskać więcej informacji na temat tego pliku, zapoznaj [się ze strukturą pliku Content_types\]. XML](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
 Plik [Content_Types]. XML jest wymagany przez Standard OPC (Open pakowanie Conventions). Aby uzyskać więcej informacji na temat OPC, zobacz [OPC: A New Standard for pakowanie danych](https://go.microsoft.com/fwlink/?LinkID=148207) w witrynie MSDN w sieci Web.
