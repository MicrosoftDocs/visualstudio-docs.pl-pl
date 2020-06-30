---
title: 'CA1020: Unikaj przestrzeni nazw z kilkoma typami | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ddd69c62eb4d6b818410a588967c1e23f164f9a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546734"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Unikaj przestrzeni nazw z małą liczbą typów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Przestrzeń nazw inna niż globalna przestrzeń nazw zawiera mniej niż pięć typów.

## <a name="rule-description"></a>Opis reguły
 Upewnij się, że każda przestrzeń nazw ma logiczną organizację i że istnieje prawidłowa przyczyna, aby umieścić typy w rozrzedzonie wypełnionym obszarze nazw. Przestrzenie nazw powinny zawierać typy, które są używane razem w większości scenariuszy. Gdy ich aplikacje wykluczają się wzajemnie, typy powinny znajdować się w oddzielnych obszarach nazw. Na przykład <xref:System.Web.UI> przestrzeń nazw zawiera typy, które są używane w aplikacjach sieci Web, a <xref:System.Windows.Forms> przestrzeń nazw zawiera typy, które są używane w [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] aplikacjach opartych na bazie. Mimo że oba obszary nazw mają typy kontrolujące aspekty interfejsu użytkownika, te typy nie są przeznaczone do użycia w tej samej aplikacji. W związku z tym znajdują się one w oddzielnych przestrzeniach nazw. Ostrożna organizacja przestrzeni nazw może być również przydatna, ponieważ zwiększa wykrywalność funkcji. Badając hierarchię przestrzeni nazw, odbiorcy biblioteki powinni mieć możliwość lokalizowania typów, które implementują funkcję.

> [!NOTE]
> Typy i uprawnienia czasu projektowania nie powinny być scalane z innymi przestrzeniami nazw w celu zachowania zgodności z tymi wskazówkami. Te typy należą do ich własnych przestrzeni nazw poniżej głównej przestrzeni nazw, a przestrzenie nazw powinny kończyć się `.Design` `.Permissions` odpowiednio i.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, spróbuj połączyć przestrzenie nazw zawierające kilka typów w pojedynczej przestrzeni nazw.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli przestrzeń nazw nie zawiera typów, które są używane z typami w innych przestrzeniach nazw, można bezpiecznie pominąć ostrzeżenie z tej reguły.
