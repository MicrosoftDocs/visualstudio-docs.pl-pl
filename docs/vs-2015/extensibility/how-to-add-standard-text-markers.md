---
title: 'Instrukcje: Dodawanie standardowych znaczników tekstu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912d5d7a225520fc825d832bf73f5cfc733a9486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780704"
---
# <a name="how-to-add-standard-text-markers"></a>Instrukcje: dodawanie standardowych znaczników tekstu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj poniższej procedury, aby utworzyć jeden z domyślnych typów znaczników tekstu dostarczonych z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytorem podstawowym.  
  
### <a name="to-create-a-text-marker"></a>Aby utworzyć znacznik tekstu  
  
1. W zależności od tego, czy używasz jednego lub dwuwymiarowego układu współrzędnych, wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodę lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodę, aby utworzyć nowy znacznik tekstu.  
  
     W tym wywołaniu metody Określ typ znacznika, zakres tekstu do utworzenia znacznika i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejs. Ta metoda zwraca wskaźnik do nowo utworzonego znacznika tekstu. Typy znaczników są pobierane z <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> wyliczenia. Określ <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejs, jeśli chcesz otrzymywać informacje o zdarzeniach znacznika.  
  
    > [!NOTE]
    > Utwórz znaczniki tekstu tylko w głównym wątku interfejsu użytkownika. Podstawowy edytor opiera się na zawartości buforu tekstu do tworzenia znaczników tekstu, a bufor tekstu nie jest bezpieczny wątkowo.  
  
## <a name="adding-a-custom-command"></a>Dodawanie polecenia niestandardowego  
 Implementacja `IVsTextMarkerClient` interfejsu i dostarczenie wskaźnika do niego ze znacznika rozszerza zachowanie znacznika na kilka sposobów. W pierwszej kolejności można podać porady dotyczące znacznika i wykonać polecenia. Umożliwia to również otrzymywanie powiadomień o zdarzeniach dla pojedynczych znaczników i utworzenie niestandardowego menu kontekstowego na znaczniku. Aby dodać niestandardowe polecenie do menu kontekstowego znacznika, należy wykonać czynności opisane w poniższej procedurze.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Aby dodać polecenie niestandardowe do menu kontekstowego  
  
1. Przed wyświetleniem menu kontekstowego środowisko wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> metodę i przekazuje wskaźnik do znacznika tekstu, którego to dotyczy, oraz liczbę elementów polecenia w menu kontekstowym.  
  
     Na przykład polecenia specyficzne dla punktu przerwania w menu kontekstowym obejmują **Usuwanie punktu przerwania** za pomocą **nowego punktu przerwania**, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Menu kontekstowe znacznika](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2. Przekaż jakiś tekst identyfikujący nazwę polecenia niestandardowego. Na przykład **usunięcie punktu przerwania** może być poleceniem niestandardowym, jeśli środowisko jeszcze go nie dostarczyło. Możesz również przejść z powrotem, niezależnie od tego, czy polecenie jest obsługiwane, dostępne i włączone i/lub przełącznik włączony. Środowisko używa tych informacji do wyświetlania polecenia niestandardowego w menu kontekstowym w prawidłowy sposób.  
  
3. Aby wykonać polecenie, środowisko wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> metodę, przekazując wskaźnik do znacznika tekstu oraz liczbę poleceń wybranych z menu kontekstowego.  
  
     Użyj tych informacji z tego wywołania, aby wykonać dowolne akcje znacznika tekstu, które wyrzuca polecenie niestandardowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie znaczników tekstowych ze starszym interfejsem API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Instrukcje: implementowanie znaczników błędów](../extensibility/how-to-implement-error-markers.md)   
 [Instrukcje: Tworzenie niestandardowych znaczników tekstu](../extensibility/how-to-create-custom-text-markers.md)   
 [Instrukcje: korzystanie ze znaczników tekstu](../extensibility/how-to-use-text-markers.md)
