---
title: 'Porady: Implementowanie znaczniki błędów | Dokumentacja firmy Microsoft'
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
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e4dd15f4cbb36ef1f81d3b7ca345a6a06bdaff4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736188"
---
# <a name="how-to-implement-error-markers"></a>Porady: Implementowanie znaczniki błędów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Znaczniki błędów (lub czerwone faliste podkreślenia) są najtrudniejsze dostosowania edytora tekstu do zaimplementowania. Jednak korzyści, które zapewniają użytkownikom usługi pakietu VSPackage może znacznie przeważają nad koszt zapewnić im. Znaczniki błędów kliknięcia zaznacz tekst, który Twoja analizatora języka jeśli uzna, że nieprawidłowe z czerwona linia falista lub faliste. Ten wskaźnik pomaga programistom wizualnie, wyświetlając nieprawidłowy kod.  
  
 Korzystanie ze znaczników tekstu do zaimplementowania czerwone faliste podkreślenia. Zgodnie z zasadą usług językowych Dodaj czerwone faliste podkreślenia w buforze tekstu jako tło — dostęp próbny na czas bezczynności, po lub w wątku w tle.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Aby zaimplementować funkcję czerwoną, falistą linią  
  
1. Zaznacz tekst, w którym chcesz umieścić czerwoną, falistą linią.  
  
2. Utworzyć znacznik o typie `MARKER_CODESENSE_ERROR`. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie standardowych znaczników tekstu](../extensibility/how-to-add-standard-text-markers.md).  
  
3. Następnie należy przekazać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> wskaźnika interfejsu.  
  
   Ten proces umożliwia również tworzenie tekst porady lub menu kontekstowego specjalne za pośrednictwem danego znacznika. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie standardowych znaczników tekstu](../extensibility/how-to-add-standard-text-markers.md).  
  
   Następujące obiekty są wymagane, przed wyświetleniem znaczniki błędów.  
  
- Analizator.  
  
- Dostawca zadań (oznacza to, że implementacja interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>) który przechowuje rekord zmiany w informacjach o wiersz w celu identyfikowania wiersze, które mają być ponownie przeanalizowany.  
  
- Filtr widoku tekstu, który przechwytuje karetki zdarzenia zmian z widoku przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) metody.  
  
  Analizator, dostawca zadań i filtr zapewniają infrastrukturę niezbędną do umożliwienia znaczniki błędów. W poniższych krokach przedstawiono proces wyświetlania znaczniki błędów.  
  
1.  W widoku, który jest filtrowana filtr uzyskuje wskaźnik do zadania skojarzonego z danymi tego widoku.  
  
    > [!NOTE]
    >  Można użyć tego samego filtru polecenia dla metody porady, uzupełnianie składni, znaczniki błędów i tak dalej.  
  
2.  Gdy filtr odbierze zdarzenie wskazujące, że zostały przeniesione do innego wiersza, aby sprawdzić błędy tworzone jest zadanie.  
  
3.  Program obsługi zadań sprawdza, czy wiersz został zmieniony. Jeśli tak, analizuje wiersza dla błędów.  
  
4.  Jeśli wystąpią błędy, dostawca zadań tworzy wystąpienia elementu zadania. To wystąpienie tworzy znacznika tekstu, który środowiska używa jako znacznik błędów w widoku tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Znaczniki tekstu przy użyciu starszej wersji interfejsu API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Porady: Dodawanie znaczników standardowy tekst](../extensibility/how-to-add-standard-text-markers.md)   
 [Porady: Tworzenie niestandardowego tekstu znaczników](../extensibility/how-to-create-custom-text-markers.md)   
 [Instrukcje: korzystanie ze znaczników tekstu](../extensibility/how-to-use-text-markers.md)

