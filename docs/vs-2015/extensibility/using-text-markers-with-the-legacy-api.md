---
title: Używanie znaczników tekstowych w starszym interfejsie API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dff5e6ecf60d389730841e99b87db584465e020
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695477"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Korzystanie ze znaczników tekstu ze starszym interfejsem API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Znacznik tekstu to swobodny zakres tekstu w buforze, który może wpływać na wyświetlanie i zachowanie regionu tekstu. Znaczniki obejmują punkty przerwania, zakładki, faliste podkreślenia i regiony tylko do odczytu. Znaczniki tekstu są zasadniczo różne od kolorowania składni. Kolorowanie składni to szybki sposób komunikowania składni języka, która jest skojarzona z regionem tekstu. Kolorowanie składni jest zazwyczaj wymagane, gdy system Windows odświeża ekran, gdy jest to ważne. Kolorowanie składni powoduje zmianę koloru tekstu. Znaczniki tekstu mogą zmieniać wiele innych właściwości tekstu. Znaczniki tekstu mogą "float" i stosować specjalne zachowanie i kolorowanie.  
  
 Ze względu na obciążenie wydajności skojarzone ze znacznikami tekstu nie należy tworzyć wielu znaczników dla buforów tekstu. Każdy znacznik jest aktualizowany za każdym razem, gdy użytkownik edytuje zawartość buforu.  
  
> [!NOTE]
> Użytkownicy mogą zmieniać kolor widocznego typu znacznika, ale nie jego kształtu i stylu. Aby uzyskać więcej informacji, zobacz [czcionki i kolory, środowisko, Opcje — okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: dodawanie standardowych znaczników tekstu](../extensibility/how-to-add-standard-text-markers.md)|Opisuje sposób dodawania standardowego typu znacznika tekstu dostarczonego przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Edytor podstawowy do widoku tekstu.|  
|[Instrukcje: implementowanie znaczników błędów](../extensibility/how-to-implement-error-markers.md)|Opisuje, jak zaimplementować wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] znacznika, który jest używany do wskazania błędów przy użyciu czerwonych falistych podkreśleń.|  
|[Instrukcje: tworzenie niestandardowych znaczników tekstu](../extensibility/how-to-create-custom-text-markers.md)|Opisuje sposób tworzenia i dodawania niestandardowego znacznika tekstu do widoku tekstu.|  
|[Instrukcje: korzystanie ze znaczników tekstu](../extensibility/how-to-use-text-markers.md)|Wyjaśnia, jak dodać znaczniki tekstu.|  
|[Wewnątrz edytora podstawowego](../extensibility/inside-the-core-editor.md)|Opisuje funkcje edytora podstawowego i zawiera szczegółowe informacje dotyczące sposobu dostosowywania edytora podstawowego.|  
|[Funkcje edytora](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Zawiera opis funkcji dostępnych w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Edytorze podstawowym.|  
  
## <a name="reference"></a>Dokumentacja  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Zapewnia jednolity mechanizm uzyskiwania informacji o konkretnym typie znacznika tekstu, niezależnie od tego, czy jest wstępnie zdefiniowany przez Edytor, czy zarejestrowany przez pakietu VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Zapewnia dostęp do i dostosowuje położenie znacznika tekstu w buforze tekstu przy użyciu współrzędnych dwuwymiarowych.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Zapewnia metody do zarządzania znacznikami tekstu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Zapewnia wywołania zwrotne do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE i innych procesów, które są używane do dostosowywania znacznika tekstu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Rozszerza funkcjonalność, która jest dostępna za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu, zapewniając dodatkowe wywołania zwrotne.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Rozszerza funkcjonalność, która jest dostępna za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu, zapewniając dodatkowe wywołania zwrotne.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Włącza typ znacznika, aby określić, czy inne typy znaczników współdzielą ten sam zestaw kolorów.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Zawiera kontekst dla znaczników tekstowych w edytorze podstawowym. Dla każdego typu znacznika tekstu, który znajduje się w edytorze Core, IDE tworzy oddzielny <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> obiekt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Program obsługi, który jest dostarczany dla znaczników, których glify obsługują edycję metodą "przeciągnij i upuść". Symbol jest ikoną wskazującą położenie znacznika.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interfejs z usługi, która udostępnia znaczniki tekstowe innym pakietów VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Zapewnia dostęp do i dostosowuje położenie znacznika tekstu w buforze tekstu przy użyciu współrzędnych jednowymiarowych. Jeśli jest to możliwe, nie używaj tego interfejsu.
