---
title: Szybkie informacje w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8bba57c0a069f515f29e02ec712e3cce7d457f95
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53908776"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Szybkie informacje w starszej wersji usługi językowej
Szybkie informacje technologii IntelliSense zawiera informacje o odpowiadającym w źródle, gdy użytkownik umieszcza karetkę w identyfikatorze i wybiera **Quick Info** z **IntelliSense** menu lub mieści wskaźnik myszy kursor nad identyfikatorem. Powoduje to etykietki narzędzia się z informacjami o tym identyfikatorze. Te informacje zazwyczaj składa się z typ identyfikatora. Gdy aparat debugowania jest aktywne, te informacje mogą obejmować bieżącą wartość. Aparat debugowania dostarcza wartości wyrażeń, gdy usługa językowa obsługuje tylko identyfikatorów.  
  
 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej, zobacz [instruktażu: Wyświetlanie etykietek narzędzi Szybkieinfo](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.  
  
 Klasy usługi języka framework (MPF) pakietu zarządzanego zapewniają pełną obsługę wyświetlania etykietki narzędzia Szybkie informacje technologii IntelliSense. To wszystko, co należy zrobić, podaj tekst, który ma być wyświetlane i włączyć funkcję Szybkie informacje.  
  
 Tekst, który ma być wyświetlany można uzyskać przez wywołanie <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizatora metody z wartością Przyczyna analizy <xref:Microsoft.VisualStudio.Package.ParseReason>. Z tego powodu Określa, że analizator, aby uzyskać informacje o typie (lub niezależnie od rodzaju jest odpowiednia do wyświetlenia w etykietce narzędzia Szybkie informacje) dla identyfikatora w lokalizacji określonej w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiektu. <xref:Microsoft.VisualStudio.Package.ParseRequest> Obiekt jest co został przekazany do <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody.  
  
 Analizator musi przeanalizować wszystko, co do pozycji w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiektu w celu określenia typów wszystkich identyfikatorów. Następnie analizator należy uzyskać identyfikator lokalizacji żądania analizy. Na koniec analizator musi przekazać dane Porada narzędzia, które są skojarzone z danym identyfikatorem do <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektu, więc ten obiekt może zwrócić tekst z <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metody.  
  
## <a name="enabling-the-quick-info-feature"></a>Włączenie funkcji Szybkie informacje  
 Aby włączyć funkcję Szybkie informacje, należy ustawić `CodeSense` i `QuickInfo` nazwanych parametrów z <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Ustaw te atrybuty <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> i <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> właściwości.  
  
## <a name="implementing-the-quick-info-feature"></a>Implementowanie funkcji Szybkie informacje  
 <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasa obsługuje operację szybkie informacje technologii IntelliSense. Gdy <xref:Microsoft.VisualStudio.Package.ViewFilter> klasa otrzymuje <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> polecenia, wywołania klasy <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda przyczynę analizy <xref:Microsoft.VisualStudio.Package.ParseReason> i położenie karetki w czasie <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Wysłano polecenie. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analizatora składni metody należy następnie przeanalizować źródła do danej lokalizacji, a następnie analizować identyfikator w podanej lokalizacji, aby określić, co jest wyświetlane w etykietce narzędzia Szybkie informacje.  
  
 Większość parsery zrobić początkowej analizy całego pliku źródłowego i zapisać wyniki w drzewo analizy. Pełna analiza odbywa się podczas <xref:Microsoft.VisualStudio.Package.ParseReason> jest przekazywany do <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody. Inne rodzaje analizy, następnie można użyć w drzewie analizy uzyskać odpowiednie informacje.  
  
 Na przykład analizy Przyczyna wartość <xref:Microsoft.VisualStudio.Package.ParseReason> można znaleźć identyfikatora w lokalizacji źródłowej i wyszukiwanie w drzewie analizy w celu uzyskania informacji o typie. Informacje o tym typie są następnie przekazywane do <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy i jest zwracany przez <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metody.