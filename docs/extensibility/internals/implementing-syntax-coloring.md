---
title: Implementowanie kolorowanki składni | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 83ce66dd6a31e3ef852feb91e2ba304e6688a723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707646"
---
# <a name="implementing-syntax-coloring"></a>Implementowanie kolorowania składni
Gdy usługa językowa zapewnia kolorowanie składni, analizator konwertuje wiersz tekstu na tablicę elementów colorable i zwraca typy tokenów odpowiadające tym elementom colorable. Analizator powinien zwracać typy tokenów, które należą do listy elementów colorable. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]wyświetla każdy element colorable w oknie kodu zgodnie z atrybutami przypisanymi przez obiekt colorizer do odpowiedniego typu tokenu.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]nie określa interfejsu analizatora, a implementacja analizatora jest całkowicie do Ciebie. Jednak domyślna implementacja analizatora jest dostępna w projekcie pakietu językowego programu Visual Studio. Dla kodu zarządzanego, struktura pakietów zarządzanych (MPF) zapewnia pełną obsługę kolorowania tekstu.

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementowania kolorowania składni, zobacz [Przewodnik: Wyróżnianie tekstu](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Kroki, po których następuje edytor w celu pokolorowania tekstu

1. Edytor pobiera colorizer wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodę na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> obiekcie.

2. Edytor wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> metodę, aby ustalić, czy colorizer wymaga stanu każdej linii, które mają być utrzymywane poza colorizer.

3. Jeśli colorizer wymaga stanu, który ma być utrzymywany <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> poza colorizer, edytor wywołuje metodę, aby uzyskać stan pierwszego wiersza.

4. Dla każdego wiersza w buforze <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> edytor wywołuje metodę, która wykonuje następujące kroki:

    1. Wiersz tekstu jest przekazywany do skanera w celu przekonwertowania tekstu na tokeny. Każdy token określa tekst tokenu i typ tokenu.

    2. Typ tokenu jest konwertowany na indeks na listę elementów colorable.

    3. Informacje tokenu jest używany do wypełnienia tablicy w taki sposób, że każdy element tablicy odpowiada znak w wierszu. Wartości przechowywane w tablicy są indeksy do listy elementów colorable.

    4. Stan na końcu wiersza jest zwracany dla każdego wiersza.

5. Jeśli colorizer wymaga stanu do utrzymania, edytor buforuje stan dla tego wiersza.

6. Edytor renderuje wiersz tekstu przy użyciu informacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> zwróconych z metody. Wymaga to następujących kroków:

    1. Dla każdego znaku w wierszu pobierz indeks elementu colorable.

    2. Jeśli używasz domyślnych elementów colorable, dostęp do listy elementów colorable edytora.

    3. W przeciwnym razie wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodę usługi języka, aby uzyskać element colorable.

    4. Użyj informacji w elementu colorable do renderowania tekstu na ekranie.

## <a name="managed-package-framework-colorizer"></a>Colorizer struktury zarządzanej pakietów
 Struktura pakietu zarządzanego (MPF) zawiera wszystkie klasy, które są wymagane do zaimplementowania colorizer. Klasa usługi języka należy <xref:Microsoft.VisualStudio.Package.LanguageService> dziedziczyć klasy i zaimplementować wymagane metody. Należy podać skaner i analizator przez <xref:Microsoft.VisualStudio.Package.IScanner> implementowanie interfejsu i zwracać wystąpienie tego interfejsu z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody (jedna <xref:Microsoft.VisualStudio.Package.LanguageService> z metod, które muszą być zaimplementowane w klasie). Aby uzyskać więcej informacji, zobacz [Kolorowanie składni w starszej usłudze językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Niestandardowe elementy z możliwością kolorowania](../../extensibility/internals/custom-colorable-items.md)
- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
