---
title: Informacje o parametrach w starszej wersji usługi językowej1 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b02db44cef8734f70f81847b224bc007fe1b4500
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114005"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informacje o parametrach w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Etykietki narzędzi IntelliSense Parameter Info zapewnia użytkownikom wskazówek na temat, gdzie się znajdują konstrukcją języka pierwszej klasy.  
  
 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie usług edytora i języka](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.  
  
## <a name="how-parameter-info-tooltips-work"></a>Jak działają parametr informacje w etykietkach narzędzi  
 Po wpisaniu instrukcji w edytorze pakietu VSPackage Wyświetla okno etykiety narzędzi małych definicją instrukcji jego wpisywania. Na przykład, jeśli typ oświadczenia Microsoft Foundation Classes (MFC) (takich jak `pMainFrame ->UpdateWindow`) i naciśnij klawisz nawias otwierający, aby rozpocząć, lista parametrów, metody, pojawi się porada wyświetlanie definicji `UpdateWindow` metody.  
  
 Etykietki narzędzi informacje o parametrze są zwykle używane w połączeniu z uzupełniania instrukcji. Są one najbardziej przydatny w przypadku języków, które mają parametry lub innych sformatowane informacji po nazwie metody lub słowa kluczowego.  
  
 Informacje o parametrach etykietki narzędzi są inicjowane przez usługę języka za pomocą polecenia zatrzymania. Przechwycenia znaków użytkownika, musi implementować obiektu usługi języka <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs i przekaż widoku tekstu, wskaźnik do Twojej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementacji, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> method in Class metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu. Filtr polecenia przechwytuje poleceń, które można wpisać w oknie kodu. Monitorowanie informacji o poleceniu, aby dowiedzieć się, kiedy należy wyświetlić informacje o parametrach dla użytkownika. Można użyć tego samego filtru polecenia do uzupełniania instrukcji, znaczniki błędów i tak dalej.  
  
 Podczas wpisywania tekstu — słowo kluczowe, dla którego usługa językowa zapewniają wskazówki, usługa językowa utworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> obiektów i wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> method in Class metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsie powiadomić środowiska IDE, aby wyświetlić wskazówkę. Tworzenie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> przy użyciu `VSLocalCreateInstance` i określając wspólna `CLSID_VsMethodTipWindow`. `VsLocalCreateInstance` jest funkcją zdefiniowaną w vsdoc.h pliku nagłówka, który wywołuje `QueryService` rejestru lokalnego i wywołania `CreateInstance` dla tego obiektu dla `CLSID_VsMethodTipWindow`.  
  
## <a name="providing-a-method-tip"></a>Zapewnianie wskazówki metody  
 Aby zapewnić wskazówki metody, należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> method in Class metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interfejsu i przekazanie do niej implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfejsu.  
  
 Gdy Twoja <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> klasy jest wywoływany, jego metody są wywoływane w następującej kolejności:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Zwraca bieżący bufor tekstowy pozycji i długości odpowiednie dane. To powoduje, że środowisko IDE będzie nie mogą zasłaniać tych danych za pomocą okna etykiety narzędzi.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Zwraca liczbę — metoda (liczony od zera indeks) mają być wyświetlane w początkowym. Na przykład jeśli można zwrócić zero, następnie pierwsza przeciążona metoda początkowo zobaczy.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Zwraca liczbę przeciążonych metod, które są stosowane w bieżącym kontekście. Jeśli zwróci wartość większą niż 1 dla tej metody, następnie widoku tekstu Wyświetla strzałek w górę i w dół dla Ciebie. Jeśli klikniesz przycisk strzałki w dół, IDE wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> metody. Jeśli klikniesz przycisk strzałki w górę, IDE wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> metody.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Tekst etykietki narzędzia Parameter Info jest tworzony podczas kilka wywołań <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> metody.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Zwraca liczbę parametrów, aby wyświetlić w metodzie.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Po powrocie liczbą metoda odpowiadające za pomocą przeciążenia, które mają być wyświetlane, ta metoda jest wywoływana, następuje wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metody.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informuje usługi języka w celu aktualizacji edytor, gdy wskazówki metody jest wyświetlana. W <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metody, wywołaj następujące czynności:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Pojawi się po wywołaniu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metody, gdy zamkniesz okno porad metody.
