---
title: Szybkie informacje w starszej wersji usługi językowej | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc8bfff0903d2ed1554cfd8b3d5b1dcf5cf0fa8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64781980"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Szybkie informacje w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Funkcja IntelliSense — szybkie informacje wyświetla informacje o identyfikatorze w źródle, gdy użytkownik umieści karetkę w identyfikatorze i wybiera **szybkie informacje** z menu **IntelliSense** lub utrzymuje wskaźnik myszy nad identyfikatorem. Powoduje to wyświetlenie etykietki narzędzia z informacjami o identyfikatorze. Te informacje zwykle składają się z typu identyfikatora. Gdy aparat debugowania jest aktywny, te informacje mogą zawierać bieżącą wartość. Aparat debugowania dostarcza wartości wyrażeń, podczas gdy usługa języka obsługuje tylko identyfikatory.  
  
 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [Przewodnik: wyświetlanie etykietek narzędzi sekcji szybkich informacji](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.  
  
 Klasy usługi języka Managed Package Framework (MPF) zapewniają pełną obsługę wyświetlania porady narzędzia do szybkiej obsługi funkcji IntelliSense. Wystarczy podać tekst do wyświetlenia i włączyć funkcję Szybkie informacje.  
  
 Tekst, który ma być wyświetlany, jest uzyskiwany przez wywołanie <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizatora metody z wartością przyczyny analizy <xref:Microsoft.VisualStudio.Package.ParseReason> . Ten powód nakazuje analizatorowi uzyskanie informacji o typie (lub dowolnego elementu, który jest wyświetlany w etykietce narzędzia szybkiej informacji) dla identyfikatora w lokalizacji określonej w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekcie. <xref:Microsoft.VisualStudio.Package.ParseRequest>Obiekt jest przekazano do <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody.  
  
 Analizator musi analizować wszystko do pozycji w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekcie, aby określić typy wszystkich identyfikatorów. Następnie analizator musi uzyskać identyfikator w lokalizacji żądania analizy. Na koniec analizator musi przekazać dane etykietki narzędzia powiązane z tym identyfikatorem do <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektu, aby obiekt mógł zwrócić tekst z <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metody.  
  
## <a name="enabling-the-quick-info-feature"></a>Włączanie funkcji Quick info  
 Aby włączyć funkcję Szybkie informacje, należy ustawić `CodeSense` `QuickInfo` Parametry i <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Te atrybuty ustawiają <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> właściwości i <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> .  
  
## <a name="implementing-the-quick-info-feature"></a>Implementowanie funkcji szybkich informacji  
 <xref:Microsoft.VisualStudio.Package.ViewFilter>Klasa obsługuje operację szybkiej informacji funkcji IntelliSense. Gdy <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasa otrzymuje <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> polecenie, Klasa wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodę z przyczyną analizy <xref:Microsoft.VisualStudio.Package.ParseReason> i lokalizacją karetki w momencie <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> wysłania polecenia. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Analizator metody musi następnie przeanalizować źródło do danej lokalizacji, a następnie przeanalizować identyfikator w podanej lokalizacji, aby określić, co ma być wyświetlane w etykietce narzędzia szybkiej informacji.  
  
 Większość analizatorów przeprowadza wstępną analizę całego pliku źródłowego i zapisuje wyniki w drzewie analizy. Zakończenie przeprowadzenia analizy odbywa się, gdy <xref:Microsoft.VisualStudio.Package.ParseReason> zostanie przekazane do <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody. Inne rodzaje analiz mogą następnie użyć drzewa analizy do uzyskania żądanych informacji.  
  
 Na przykład wartość przyczyny analizy <xref:Microsoft.VisualStudio.Package.ParseReason> może znaleźć identyfikator w lokalizacji źródłowej i wyszukać ją w drzewie analizy, aby uzyskać informacje o typie. Informacje tego typu są następnie przesyłane do <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy i zwracane przez <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metodę.
