---
title: 'Porady: Dodawanie znaczników standardowy tekst | Dokumentacja firmy Microsoft'
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
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 54dcfc9a1952dc0cd816c2ce7ad83cd8355f0066
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779479"
---
# <a name="how-to-add-standard-text-markers"></a>Porady: Dodawanie znaczników standardowy tekst
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniższa procedura umożliwia utworzenie jednej z domyślnych typów znacznika tekstu, wyposażone w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytorze podstawowych funkcji.  
  
### <a name="to-create-a-text-marker"></a>Aby utworzyć znacznika tekstu  
  
1.  W zależności od tego, czy używany jest jeden lub dwa - wymiarowej współrzędnych, wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metody lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodę w celu utworzenia nowego znacznika tekstu.  
  
     W tym wywołaniu metody, określ typ znacznika, zakres tekstu do tworzenia znacznika i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu. Ta metoda zwraca wskaźnik do znacznika nowo utworzony tekstu. Typy znacznika są pobierane z <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> wyliczenia. Określ <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu, jeśli ma być powiadamiany o znacznika zdarzenia.  
  
    > [!NOTE]
    >  Utwórz znaczników tekstu w głównym wątku interfejsu użytkownika tylko. Podstawowy edytor, który opiera się na zawartość bufor tekstowy do utworzenia znaczników tekstu i bufor tekstowy nie jest bezpieczny dla wątków.  
  
## <a name="adding-a-custom-command"></a>Dodawanie polecenia niestandardowego  
 Implementowanie `IVsTextMarkerClient` interfejsu i zapewnianie wskaźnika z znacznik poprawia zachowanie znacznik na kilka sposobów. Po pierwsze dzięki temu można zapewnić porady dla Twojej znacznika oraz do wykonywania poleceń. To umożliwia także otrzymywać powiadomienia o zdarzeniach dla poszczególnych znaczników oraz aby utworzyć menu kontekstowego za pośrednictwem znacznika. Poniższa procedura umożliwia dodawanie polecenia niestandardowego do menu kontekstowego znacznika.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Aby dodać niestandardowe polecenia do menu kontekstowego  
  
1.  Menu kontekstowe jest wyświetlane, środowisko wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> metody i przebiegów możesz wskaźnik do znacznika tekstu na i numer elementu polecenia w menu kontekstowym.  
  
     Na przykład zawierać polecenia specyficzne dla punktu przerwania z menu kontekstowego **Usuń punkt przerwania** za pośrednictwem **nowego punktu przerwania**wyświetlane w poniższy zrzut ekranu.  
  
     ![Menu kontekstowe znacznika](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  Przesłać tekst, który identyfikuje nazwę polecenia niestandardowe. Na przykład **Usuń punkt przerwania** może być polecenie niestandardowe, jeśli środowisko nie już podał go. Możesz też przekazać ponownie tego, czy polecenie jest obsługiwane, dostępna i włączona i/lub przełącz wł. / wył. Środowisko używa tych informacji do wyświetlania polecenia niestandardowego menu kontekstowego w prawidłowy sposób.  
  
3.  Można wykonać polecenia wywołania środowiska <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> metody przekazywania wskaźnika znacznika tekst i liczby wybrane z menu kontekstowego polecenie.  
  
     Dzięki tym informacjom tego wywołania do wykonania, mówią, niezależnie od akcji znacznika tekstu polecenia niestandardowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Znaczniki tekstu przy użyciu starszej wersji interfejsu API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Porady: Implementowanie znaczniki błędów](../extensibility/how-to-implement-error-markers.md)   
 [Porady: Tworzenie niestandardowego tekstu znaczników](../extensibility/how-to-create-custom-text-markers.md)   
 [Instrukcje: korzystanie ze znaczników tekstu](../extensibility/how-to-use-text-markers.md)

