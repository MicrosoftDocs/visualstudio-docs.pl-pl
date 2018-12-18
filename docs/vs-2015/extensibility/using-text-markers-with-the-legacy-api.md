---
title: Znaczniki tekstu przy użyciu starszej wersji interfejsu API | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 600e9635fb0ee5ea78226277860ac41e183f47b5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745905"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Znaczniki tekstu przy użyciu starszej wersji interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Znacznik tekstu jest ruchomy zakres tekstu w buforze, które mogą mieć wpływ na wyświetlanie i zachowanie region tekstu. Znaczniki zawierają punkty przerwania, zakładek, faliste podkreślenia i regionów tylko do odczytu. Znaczniki tekstu po prostu różnią się od kolorowanie składni. Kolorowanie składni to szybki sposób komunikowania się składni języka, która jest skojarzone z regionem tekstu. Kolorowanie składni ogólnie jest wymagany, gdy Windows odświeża ekran, gdy szybkość jest istotna. Kolorowanie składni zmienia kolor tekstu. Znaczniki tekst można zmienić innych właściwości tekstu. Znaczniki tekstu można "float" i zastosować specjalnego zachowania i kolorowania.  
  
 Ze względu na zmniejszenie wydajności związane ze znacznikami tekst nie należy tworzyć wielu znaczników swoje bufory tekstu. Każdy znacznik jest aktualizowana w każdym razem, gdy użytkownik dokona edycji zawartości buforu.  
  
> [!NOTE]
>  Użytkownicy mogą zmieniać kolor typu znacznika widoczne, ale nie jego kształtu i stylu. Aby uzyskać więcej informacji, zobacz [czcionki i kolory, środowisko, opcje, okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: dodawanie standardowych znaczników tekstu](../extensibility/how-to-add-standard-text-markers.md)|W tym artykule opisano sposób dodawania tekstu standardowego typu znaczników, dostarczone przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytorze podstawowych funkcji do widoku tekstu.|  
|[Instrukcje: implementowanie znaczników błędów](../extensibility/how-to-implement-error-markers.md)|W tym artykule opisano sposób wdrażania wystąpienia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] znacznik, który służy do sygnalizowania błędów przy użyciu czerwone faliste podkreślenia.|  
|[Instrukcje: tworzenie niestandardowych znaczników tekstu](../extensibility/how-to-create-custom-text-markers.md)|W tym artykule opisano, jak utworzyć i dodać typ znacznika niestandardowego tekstu do widoku tekstu.|  
|[Instrukcje: korzystanie ze znaczników tekstu](../extensibility/how-to-use-text-markers.md)|Wyjaśnia, jak dodawać znaczniki tekstu.|  
|[Wewnątrz edytora podstawowego](../extensibility/inside-the-core-editor.md)|Opisuje funkcje edytora podstawowe i szczegółowe informacje na temat sposobu dostosowywania podstawowy edytor.|  
|[Funkcje edytora](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|W tym artykule opisano funkcje dostępne w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytorze podstawowych funkcji.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Udostępnia mechanizm jednolitego uzyskiwania informacji na temat typu znacznika określonym tekstem, czy wstępnie zdefiniowane przez Edytor lub zarejestrowany przez funkcję pakietu VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Zapewnia dostęp do, a następnie dopasowuje pozycję znacznika tekstu w buforze tekstu przy użyciu dwuwymiarowe współrzędne.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Udostępnia metody dla zarządzania znaczników tekstu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Umożliwia wywołania zwrotne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE i inne procesy, które są używane do dostosowywania znacznika tekstu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Rozszerza funkcjonalność, która jest dostępna za pośrednictwem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu, zapewniając dodatkowe wywołania zwrotne.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Rozszerza funkcjonalność, która jest dostępna za pośrednictwem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu, zapewniając dodatkowe wywołania zwrotne.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Włącza typ znacznika ustalić, czy innych typów znaczników udostępnić ten sam zestaw kolorów.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Udostępnia kontekst dla znaczników tekstu w edytorze podstawowych. Dla każdego typu znacznika tekstu, który znajduje się w edytorze podstawowych, środowisko IDE tworzy oddzielny <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> obiektu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Program obsługi, który jest udostępniany dla znaczników, którego symbole obsługi przeciągania i upuszczania do edycji. Glif znajduje się ikona, wskazującą położenie znaczników.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interfejs z usługą, która zawiera tekst znaczniki do innych pakietów VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Zapewnia dostęp do, a następnie dopasowuje pozycję znacznika tekstu w buforze tekstu za pomocą współrzędnych jednowymiarowa. Jeśli jest to możliwe, należy używać tego interfejsu.

