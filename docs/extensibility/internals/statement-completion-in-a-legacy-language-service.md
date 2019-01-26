---
title: Uzupełnianie instrukcji w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0310f515a444d0ff68fe971463602c484763848b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965682"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Uzupełnianie instrukcji w starszej wersji usługi językowej
Uzupełnianie instrukcji jest procesem, za pomocą którego usługa językowa ułatwiają zakończyć słowem kluczowym języka lub element, który zostały uruchomione, wpisz w edytorze podstawowych. W tym temacie omówiono, jak działa uzupełniania instrukcji i sposobie jego implementowania w usłudze języka.  
  
 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej na temat nowych sposobem realizowania uzupełniania instrukcji, zobacz [instruktażu: Wyświetlanie uzupełniania instrukcji](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.  
  
## <a name="implementing-statement-completion"></a>Implementowanie uzupełnianie instrukcji  
 W edytorze podstawowych uzupełniania instrukcji aktywuje specjalny interfejs użytkownika, który interaktywnie pomaga łatwo i szybko napisać kod. Uzupełnianie instrukcji pomaga, wyświetlając odpowiednie obiekty lub klasy, gdy są one potrzebne, co pozwala uniknąć, trzeba pamiętać określone elementy lub do wyszukania w temacie pomocy odwołania.  
  
 Aby zaimplementować uzupełniania instrukcji, język musi mieć wyzwalacz uzupełniania instrukcji, można przeanalizować. Na przykład [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] używa operatora kropki (.), podczas gdy [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] używa strzałka (->) — operator. Usługa języka można użyć więcej niż jeden wyzwalacz do zainicjowania uzupełniania instrukcji. Te wyzwalacze są programowane w filtrze polecenia.  
  
## <a name="command-filters-and-triggers"></a>Polecenie filtrów i wyzwalaczy  
 Polecenie Filtry przechwycić wystąpień wyzwalacza lub wyzwalaczy. Aby dodać filtr polecenia w widoku, należy zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs i dołączyć go do widoku przez wywołanie metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody. Można użyć tego samego filtru polecenia (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) dla wszystkich aspektów języka usługi, takie jak uzupełnianie składni, znaczniki błędów i porady dotyczące metody. Aby uzyskać więcej informacji, zobacz [poleceń usługi języka Legacy przechwytuje](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Po wprowadzeniu wyzwalacz w edytorze — w szczególności buforu tekstu — usługi języka następnie wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody. Powoduje to wyświetlenie interfejsu użytkownika, aby użytkownik może wybrać spośród kandydatów uzupełnianie instrukcji w edytorze. Ta metoda wymaga implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> i <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> flagi jako parametry. Zostanie wyświetlona lista elementów uzupełniania przewijania pola listy. Jako użytkownik będzie nadal występował, wpisując, wybór w obrębie pola listy jest zaktualizowana w celu odzwierciedlenia wpisany najlepiej dopasowany do ostatnich znaków. Podstawowy edytor implementuje interfejs użytkownika uzupełniania instrukcji, ale usługa językowa musi implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfejsu, aby zdefiniować zestaw Release candidate elementy uzupełniania instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przechwytywanie poleceń starszej wersji usługi językowej](../../extensibility/internals/intercepting-legacy-language-service-commands.md)