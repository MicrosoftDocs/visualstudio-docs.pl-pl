---
title: Informacje o parametrach w starszej usłudze językowej1 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c26073252aae5434ba5a8197955948d0d9ec883d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706799"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informacje o parametrach w starszej wersji usługi językowej
Etykietka narzędzia Informacje o parametrach IntelliSense zawiera wskazówki dotyczące tego, gdzie znajdują się w konstrukcji języka.

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [Rozszerzanie edytora i usług językowych](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

## <a name="how-parameter-info-tooltips-work"></a>Jak działają etykietki informacji o parametrach
 Po wpisaniu instrukcji w edytorze, VSPackage wyświetla małe okno etykietki narzędzia zawierające definicję instrukcji wpisywane. Na przykład jeśli wpiszesz instrukcję Microsoft Foundation Classes `pMainFrame ->UpdateWindow`(MFC) (na przykład) i naciśnij klucz nawiasu otwierającego, `UpdateWindow` aby rozpocząć wyświetlanie parametrów listy, pojawi się wskazówka metody wyświetlająca definicję metody.

 Etykietki narzędzi informacje o parametrach są zwykle używane w połączeniu z uzupełnianiami instrukcji. Są one najbardziej przydatne w językach, które mają parametry lub inne sformatowane informacje po nazwie metody lub słowa kluczowego.

 Etykietki narzędzi Informacje o parametrach są inicjowane przez usługę języka za pomocą przechwytywania poleceń. Aby przechwycić znaki użytkownika, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiekt usługi języka musi zaimplementować interfejs i przekazać widok tekstu wskaźnik do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementacji, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodę w interfejsie. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Filtr polecenia przechwytuje polecenia wpisywane w oknie kodu. Monitoruj informacje o poleceniu, aby wiedzieć, kiedy mają być wyświetlane informacje o parametrach dla użytkownika. Można użyć tego samego filtru poleceń do uzupełniania instrukcji, znaczników błędów i tak dalej.

 Po wpisaniu słowa kluczowego, dla którego usługa języka może <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> dostarczyć wskazówki, a następnie usługa języka tworzy obiekt i wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodę w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsie, aby powiadomić IDE, aby wyświetlić wskazówkę. Utwórz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> obiekt `VSLocalCreateInstance` przy użyciu i `CLSID_VsMethodTipWindow`określaniu coclass . `VsLocalCreateInstance`jest funkcją zdefiniowaną w pliku nagłówka `QueryService` vsdoc.h, `CreateInstance` która wywołuje `CLSID_VsMethodTipWindow`rejestr lokalny i wywołuje ten obiekt dla pliku .

## <a name="providing-a-method-tip"></a>Dostarczanie końcówki metody
 Aby zapewnić wskazówka metody, wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodę w interfejsie, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> przekazując go implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfejsu.

 Gdy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> klasa jest wywoływana, jego metody są wywoływane w następującej kolejności:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Zwraca położenie i długość odpowiednich danych w bieżącym buforze tekstowym. To nakazuje IDE nie zasłaniać tych danych z okna etykietki narzędzia.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Zwraca numer metody (indeks oparty na wartości zero), który ma być początkowo wyświetlany. Na przykład jeśli zwrócisz zero, początkowo zostanie przedstawiona pierwsza przeciążona metoda.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Zwraca liczbę przeciążonych metod, które mają zastosowanie w bieżącym kontekście. Jeśli zwrócisz wartość większą niż 1 dla tej metody, w widoku tekstowym zostaną wyświetlone strzałki w górę i w dół. Po kliknięciu strzałki w dół, IDE wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> metodę. Po kliknięciu strzałki w górę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> IDE wywołuje metodę.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Tekst etykietki narzędzia Informacje o parametrach jest <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> konstruowany podczas kilku wywołań i metod. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Zwraca liczbę parametrów wyświetlanych w metodzie.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Jeśli zwrócisz numer metody odpowiadający przeciążeniu, które chcesz wyświetlić, ta <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metoda jest wywoływana, a następnie wywołanie metody.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Informuje usługę językową, aby zaktualizować edytor, gdy jest wyświetlana wskazówka metody. W <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metodzie wywołaj następujące połączenia:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Otrzymasz wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metody po zamknięciu okna poradki metody.
