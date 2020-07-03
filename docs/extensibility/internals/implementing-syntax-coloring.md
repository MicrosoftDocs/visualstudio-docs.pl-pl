---
title: Implementowanie kolorowania składni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb3f26f59d7cbc994da1d2537e0ab352ce12205e
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905203"
---
# <a name="implementing-syntax-coloring"></a>Implementowanie kolorowania składni
Gdy usługa językowa zapewnia kolorowanie składni, Analizator konwertuje wiersz tekstu na tablicę elementów z możliwością przykolorowania i zwraca typy tokenów odpowiadające tym elementom, które można przykolorować. Analizator powinien zwrócić typy tokenów, które należą do listy elementów z możliwością koloru. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]wyświetla każdy element, który można kolorować w oknie kodu zgodnie z atrybutami przypisanymi przez obiekt Koloruj do odpowiedniego typu tokenu.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]nie określa interfejsu analizatora i implementacja analizatora jest całkowicie do Ciebie. Jednak domyślna implementacja analizatora jest dostępna w projekcie pakietu języka programu Visual Studio. Dla kodu zarządzanego, Struktura pakietu zarządzanego (MPF) zapewnia pełną obsługę kolorowania tekstu.

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji kolorowania składni, zobacz [Przewodnik: podświetlanie tekstu](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Kroki, po których następuje edytor do kolorowania tekstu

1. Edytor pobiera kolor, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodę dla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> obiektu.

2. Edytor wywołuje metodę, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> Aby określić, czy kolorowanie wymaga stanu każdego wiersza, który ma być obsługiwany poza kolorem.

3. Jeśli kolor, który ma być obsługiwany poza kolorem, Edytor wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> metodę w celu uzyskania stanu pierwszego wiersza.

4. Dla każdego wiersza w buforze, Edytor wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodę, wykonując następujące czynności:

    1. Wiersz tekstu jest przesyłany do skanera w celu przekonwertowania tekstu na tokeny. Każdy token Określa tekst tokenu i typ tokenu.

    2. Typ tokenu jest konwertowany na indeks na listę elementów z możliwością przydzielenia.

    3. Informacje o tokenach są używane do wypełniania tablicy w taki sposób, że każdy element tablicy odpowiada znakowi w wierszu. Wartości przechowywane w tablicy są indeksami na liście elementy, które mogą być kolorowe.

    4. Stan na końcu wiersza jest zwracany dla każdego wiersza.

5. Jeśli kolor jest wymagany do utrzymania stanu, Edytor buforuje stan dla tego wiersza.

6. Edytor renderuje wiersz tekstu przy użyciu informacji zwracanych z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody. Wymaga to wykonania następujących czynności:

    1. Dla każdego znaku w wierszu Pobierz indeks elementu, który można kolorować.

    2. W przypadku używania domyślnych elementów z możliwością kolorowania można uzyskać dostęp do listy elementów z możliwością kolorowania edytora.

    3. W przeciwnym razie Wywołaj metodę języka w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> celu uzyskania elementu z możliwością kolorowania.

    4. Użyj informacji z elementu kolorowego, aby renderować tekst na ekranie.

## <a name="managed-package-framework-colorizer"></a>Kolorowanie struktury pakietu zarządzanego
 Struktura pakietu zarządzanego (MPF) udostępnia wszystkie klasy, które są wymagane do zaimplementowania Kolorka. Klasa usługi językowej powinna dziedziczyć <xref:Microsoft.VisualStudio.Package.LanguageService> klasę i zaimplementować wymagane metody. Należy dostarczyć skaner i analizator składni przez implementację <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu i zwrócić wystąpienie tego interfejsu z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody (jedną z metod, które muszą być zaimplementowane w <xref:Microsoft.VisualStudio.Package.LanguageService> klasie). Aby uzyskać więcej informacji, zobacz [kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Niestandardowe elementy z możliwością kolorowania](../../extensibility/internals/custom-colorable-items.md)
- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
