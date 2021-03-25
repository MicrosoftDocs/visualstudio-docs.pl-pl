---
title: Informacje o parametrach w starszej wersji językowej Service1 | Microsoft Docs
description: Dowiedz się, jak zaimplementować etykietkę narzędzia informacji o parametrach IntelliSense, która zapewnia użytkownikom wskazówki w starszej wersji usługi językowej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4dade924ef89be22161c598ba0ae64084c0697ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061150"
---
# <a name="parameter-info-in-a-legacy-language-service-1"></a>Informacje o parametrach w starszej wersji usługi językowej 1
Etykietka narzędzia informacji o parametrach IntelliSense udostępnia użytkownikom wskazówki dotyczące tego, gdzie znajdują się w konstrukcji językowej.

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie edytora i usług językowych](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

## <a name="how-parameter-info-tooltips-work"></a>Jak działają etykietki narzędzi informacji o parametrach
 Po wpisaniu instrukcji w edytorze pakietu VSPackage wyświetla małe okno etykietki narzędzi zawierające definicję wpisanej instrukcji. Na przykład, jeśli wpiszesz instrukcję Microsoft Foundation Classes (MFC), `pMainFrame ->UpdateWindow` a następnie naciśniesz klawisz otwierającego nawiasu, aby rozpocząć wyświetlanie parametrów, zostanie wyświetlona etykietka metody wyświetlająca definicję `UpdateWindow` metody.

 Etykietki narzędzi informacji o parametrach są zwykle używane w połączeniu z uzupełnianiem instrukcji. Są one najbardziej przydatne w przypadku języków, które mają parametry lub inne sformatowane informacje po nazwie metody lub słowie kluczowym.

 Etykietki narzędzi informacji o parametrach są inicjowane przez usługę języka za pomocą przechwycenia polecenia. Aby przechwycić znaki użytkownika, obiekt usługi językowej musi implementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs i przekazać tekst do swojej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementacji, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodę w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsie. Filtr polecenia przechwytuje polecenia wpisane do okna kod. Monitoruj informacje o poleceniu, aby dowiedzieć się, kiedy mają być wyświetlane informacje o parametrach. Tego samego filtru poleceń można użyć do uzupełniania instrukcji, znaczników błędów i tak dalej.

 Po wpisaniu słowa kluczowego, dla którego usługa języka może udostępniać wskazówki, usługa językowa tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> obiekt i wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodę w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsie, aby powiadomić IDE o wyświetleniu wskazówki. Utwórz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> Obiekt przy użyciu `VSLocalCreateInstance` i określ klasy coclass `CLSID_VsMethodTipWindow` . `VsLocalCreateInstance` jest funkcją zdefiniowaną w pliku nagłówka vsdoc. h, która wywołuje `QueryService` lokalny rejestr i wywołuje dla `CreateInstance` tego obiektu `CLSID_VsMethodTipWindow` .

## <a name="providing-a-method-tip"></a>Podawanie porady metody
 Aby zapewnić wskazówkę metody, wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodę w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interfejsie, przekazując ją do implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfejsu.

 Po <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> wywołaniu klasy jego metody są wywoływane w następującej kolejności:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Zwraca pozycję i długość odpowiednich danych w bieżącym buforze tekstu. Powoduje to, że IDE nie zasłania tych danych za pomocą okna etykietki narzędzia.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Zwraca numer metody (indeks oparty na zero), który ma być początkowo wyświetlany. Na przykład, jeśli zwracasz zero, początkowo zostanie przedstawiona pierwsza przeciążona metoda.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Zwraca liczbę przeciążonych metod, które są stosowane w bieżącym kontekście. Jeśli powrócisz wartość większą niż 1 dla tej metody, w widoku tekstu zostaną wyświetlone strzałki w górę i w dół. Jeśli klikniesz strzałkę w dół, IDE wywoła <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> metodę. Jeśli klikniesz strzałkę w górę, IDE wywoła <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> metodę.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Tekst etykietki narzędzia informacje o parametrach jest konstruowany podczas kilku wywołań <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> metod i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> .

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Zwraca liczbę parametrów, które mają być wyświetlane w metodzie.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Jeśli zwracasz numer metody odpowiadający przeciążeniu, które chcesz wyświetlić, ta metoda jest wywoływana, a następnie wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metody.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Informuje usługę języka w celu zaktualizowania edytora, gdy zostanie wyświetlona etykietka metody. W <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metodzie Wywołaj następujące polecenie:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>Po zamknięciu okna etykietki metody zostanie odebrane wywołanie metody.
