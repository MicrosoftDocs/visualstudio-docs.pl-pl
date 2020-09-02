---
title: 'Instrukcje: implementowanie znaczników błędów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2af9e0765fb5bc73a35bebfc2f50f5d2a41122d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64803611"
---
# <a name="how-to-implement-error-markers"></a>Instrukcje: implementowanie znaczników błędów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Znaczniki błędów (lub czerwone faliste podkreślenie) są najbardziej trudne do wdrożenia przez Edytor tekstu. Korzyści płynące dla użytkowników pakietu VSPackage mogą jednak znacznie obważyć koszty. Znaczniki błędów podkreślają tekst, który jest uznawany za nieprawidłowy przez parser języka, z falistej lub czerwoną linią falistą. Ten wskaźnik pomaga programistom wizualnie wyświetlać nieprawidłowy kod.  
  
 Użyj znaczników tekstowych, aby zaimplementować czerwoną falistą podkreślenie. W ramach zasady usługi językowe dodają czerwoną falistą podkreślenie do bufora tekstowego jako przebieg w tle, w czasie bezczynności lub w wątku w tle.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Aby zaimplementować czerwoną falistą funkcję podkreślenia  
  
1. Zaznacz tekst, pod którym chcesz umieścić czerwoną falistą podkreślenie.  
  
2. Utwórz znacznik typu `MARKER_CODESENSE_ERROR` . Aby uzyskać więcej informacji, zobacz [How to: Add Standard Text Marks](../extensibility/how-to-add-standard-text-markers.md).  
  
3. Po tym celu Przekaż <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> wskaźnik interfejsu.  
  
   Ten proces umożliwia również tworzenie tekstu TIP lub specjalnego menu kontekstowego dla danego znacznika. Aby uzyskać więcej informacji, zobacz [How to: Add Standard Text Marks](../extensibility/how-to-add-standard-text-markers.md).  
  
   Poniższe obiekty są wymagane, aby można było wyświetlić znaczniki błędów.  
  
- Analizator składni.  
  
- Dostawca zadań (czyli implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> ), który przechowuje rekord zmian w informacjach o wierszu w celu zidentyfikowania wierszy, które mają być ponownie analizowane.  
  
- Filtr widoku tekstu, który przechwytuje zdarzenia zmiany karetki z widoku za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A> metody).  
  
  Analizator, dostawca zadań i filtr zapewniają infrastrukturę niezbędną do zapewnienia, że znaczniki błędów mogą być możliwe. Poniższe kroki zapewniają proces wyświetlania znaczników błędów.  
  
1. W filtrowanym widoku filtr uzyskuje wskaźnik do dostawcy zadań skojarzonego z danymi tego widoku.  
  
    > [!NOTE]
    > Tego samego filtru poleceń można użyć do etykietek metod, uzupełniania instrukcji, znaczników błędów i tak dalej.  
  
2. Gdy filtr odbierze zdarzenie wskazujące, że przeniesiono do innego wiersza, zadanie jest tworzone w celu sprawdzenia pod kątem błędów.  
  
3. Procedura obsługi zadań sprawdza, czy wiersz jest zanieczyszczony. Jeśli tak, analizuje wiersz pod kątem błędów.  
  
4. Jeśli zostaną znalezione błędy, dostawca zadań tworzy wystąpienie elementu zadania. To wystąpienie powoduje utworzenie znacznika tekstu, którego środowisko używa jako znacznika błędu w widoku tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie znaczników tekstowych ze starszym interfejsem API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Instrukcje: Dodawanie standardowych znaczników tekstu](../extensibility/how-to-add-standard-text-markers.md)   
 [Instrukcje: Tworzenie niestandardowych znaczników tekstu](../extensibility/how-to-create-custom-text-markers.md)   
 [Instrukcje: korzystanie ze znaczników tekstu](../extensibility/how-to-use-text-markers.md)
