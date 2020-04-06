---
title: Szybkie informacje w starszej usłudze językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d070c607313b406f036a5b6f071eaa371070408
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705943"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Szybkie informacje w starszej wersji usługi językowej
Funkcja IntelliSense Quick Info wyświetla informacje o identyfikatorze w źródle, gdy użytkownik umieszcza karetkę w identyfikatorze i wybiera **szybkie informacje** z menu **IntelliSense** lub trzyma kursor myszy nad identyfikatorem. Powoduje to, że etykietka narzędzia pojawia się z informacjami o identyfikatorze. Te informacje zazwyczaj składają się z typu identyfikatora. Gdy aparat debugowania jest aktywny, informacje te mogą zawierać bieżącą wartość. Aparat debugowania dostarcza wartości wyrażeń, podczas gdy usługa języka obsługuje tylko identyfikatory.

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [Przewodnik: Wyświetlanie etykietek narzędzi QuickInfo](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

 Klasy usługi języka zarządzanej struktury pakietów (MPF) zapewniają pełną obsługę wyświetlania porad narzędzia IntelliSense Quick Info. Wszystko, co musisz zrobić, to podać tekst, który ma być wyświetlany i włączyć funkcję szybkich informacji.

 Tekst, który ma być wyświetlany, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> jest uzyskiwany przez wywołanie <xref:Microsoft.VisualStudio.Package.ParseReason>analizatora metody z wartością przyczyny analizy . Z tego powodu informuje analizatora, aby uzyskać informacje o typie (lub cokolwiek jest odpowiednie do wyświetlania <xref:Microsoft.VisualStudio.Package.ParseRequest> w poradniku narzędzia Szybkie informacje) dla identyfikatora w lokalizacji określonej w obiekcie. Obiekt <xref:Microsoft.VisualStudio.Package.ParseRequest> jest to, co <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> zostało przekazane do metody.

 Analizator musi przeanalizować wszystko do pozycji w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekcie w celu określenia typów wszystkich identyfikatorów. Następnie analizator musi uzyskać identyfikator w lokalizacji żądania analizy. Na koniec analizator musi przekazać dane poradnika narzędzia skojarzone <xref:Microsoft.VisualStudio.Package.AuthoringScope> z tym identyfikatorem do obiektu, aby obiekt mógł zwrócić tekst z <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metody.

## <a name="enabling-the-quick-info-feature"></a>Włączanie funkcji szybkich informacji
 Aby włączyć funkcję Szybkich informacji, `CodeSense` należy `QuickInfo` ustawić parametry <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>i nazwane . Te atrybuty <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> ustawić i właściwości.

## <a name="implementing-the-quick-info-feature"></a>Implementowanie funkcji szybkich informacji
 Klasa <xref:Microsoft.VisualStudio.Package.ViewFilter> obsługuje intellisense szybkie informacje operacji. Gdy <xref:Microsoft.VisualStudio.Package.ViewFilter> klasa odbiera <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> polecenie, klasa <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> wywołuje metodę z powodu <xref:Microsoft.VisualStudio.Package.ParseReason> analizy i lokalizacji cieszy <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> w czasie, gdy polecenie zostało wysłane. Analizator <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody musi następnie przeanalizować źródło do danej lokalizacji, a następnie przeanalizować identyfikator w danej lokalizacji, aby określić, co ma być wyświetlane w poradce narzędzia Szybkie informacje.

 Większość analizatorów wykonać wstępną analizę całego pliku źródłowego i przechowywać wyniki w drzewie analizy. Pełna analiza przeprowadzana jest <xref:Microsoft.VisualStudio.Package.ParseReason> po <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> przejściu do metody. Inne rodzaje analizowania można następnie użyć drzewa analizy, aby uzyskać żądane informacje.

 Na przykład wartość przyczyny analizy <xref:Microsoft.VisualStudio.Package.ParseReason> można znaleźć identyfikator w lokalizacji źródłowej i wyszukać go w drzewie analizy, aby uzyskać informacje o typie. Informacje o typie są <xref:Microsoft.VisualStudio.Package.AuthoringScope> następnie przekazywane do <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> klasy i są zwracane przez metodę.
