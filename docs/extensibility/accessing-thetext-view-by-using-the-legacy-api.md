---
title: Dostęp do theText widoku przy użyciu starszej wersji interfejsu API | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a52ba7fa7e57e63f13cfe502a46d54071ee82591
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313663"
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