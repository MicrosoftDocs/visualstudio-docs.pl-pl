---
title: Dostęp do theText widoku przy użyciu starszej wersji interfejsu API | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bce39d8ae736d9f7dcda8b18198053f90933b811
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62892166"
---
# <a name="access-the-text-view-by-using-the-legacy-api"></a>Dostęp do widoku tekstu przy użyciu starszej wersji interfejsu API
Widok tekstu jest prezentacji tekst, który znajduje się w buforze tekstu. Można uzyskać dostęp do widoku tekstu przy użyciu starszej wersji interfejsu API, jak pokazano w poniższej sekcji.

## <a name="text-view-object"></a>Obiekt widoku tekstu
 Każdy widok jest skojarzony z buforu tekstu, a widok jest oknem na dane w buforze. Na poniższym diagramie przedstawiono kluczowe interfejsy obiekt widoku tekstu, który jest reprezentowany przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.

 ![Obiekt widoku tekstu w programie Visual Studio](../extensibility/media/vstextview.gif)

 Widok jest sposób przedstawiania tekstu w buforze. Obejmuje funkcje, takie jak zawijania słów oraz Tworzenie konspektu, tak, aby wyświetlić w widoku nie jest dokładnie reprezentacja tekstu w buforze.

 Widok umożliwia innych usług lub procesów przechwycenia przychodzących poleceń i wykonywania względem nich działań przed widoku działa na nich. Najbardziej typowe usługi, aby to zrobić, to usługa języka. Usługa języka może być konieczne, na przykład przechwycić polecenie dla klawisz ENTER, aby zapewniają niestandardowe wcięcia tekstu porady zachowanie lub narzędzia.

## <a name="add-functionality-to-the-text-view"></a>Dodawanie funkcji do widoku tekstu
 Możesz dostosować zachowanie widoku tekstu dzięki obsłudze określonych naciśnięć klawiszy. Przechwycenia naciśnięcia klawiszy, możesz wdrożyć <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> na obiekt i podaj element docelowy polecenia (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) do monitorowania i przecięcia poleceń.

 Widok tekstu korzysta z architektury kolejne polecenia filtrów. Nowe filtry polecenia (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiektów) są dodawane do sekwencji, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody.

 Powiadamianie o zdarzeniach dla widoku tekstu znajduje się za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents> interfejsu. Implementuje ten interfejs objektu klienta, aby otrzymywać powiadomienia o zmianach w widoku tekstu. Udostępnianie tego interfejsu, aby wyświetlić tekst przy użyciu <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfejsu na widok tekstu, aby otrzymywać powiadomienia o zmianach w widoku.

## <a name="see-also"></a>Zobacz także

- [Zmienianie ustawień widoku przy użyciu starszej wersji interfejsu API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)
- [Ustawienia globalne monitorowanie za pomocą Menedżera tekstu](../extensibility/using-the-text-manager-to-monitor-global-settings.md)