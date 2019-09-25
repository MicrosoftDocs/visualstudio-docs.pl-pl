---
title: 'CA1020: Unikaj przestrzeni nazw z małą liczbą typów'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e5c50f607253304b05dd7ab9350646a0df05e70
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236232"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Unikaj przestrzeni nazw z małą liczbą typów

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Przestrzeń nazw inna niż globalna przestrzeń nazw zawiera mniej niż pięć typów.

## <a name="rule-description"></a>Opis reguły

Upewnij się, że każda przestrzeń nazw ma logiczną organizację i że istnieje prawidłowa przyczyna, aby umieścić typy w rozrzedzonie wypełnionym obszarze nazw. Przestrzenie nazw powinny zawierać typy, które są używane razem w większości scenariuszy. Gdy ich aplikacje wykluczają się wzajemnie, typy powinny znajdować się w oddzielnych obszarach nazw. Na przykład <xref:System.Web.UI> przestrzeń nazw zawiera typy, które są używane w aplikacjach sieci Web, <xref:System.Windows.Forms> a przestrzeń nazw zawiera typy, które są [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]używane w aplikacjach opartych na bazie. Mimo że oba obszary nazw mają typy kontrolujące aspekty interfejsu użytkownika, te typy nie są przeznaczone do użycia w tej samej aplikacji. W związku z tym znajdują się one w oddzielnych przestrzeniach nazw. Ostrożna organizacja przestrzeni nazw może być również przydatna, ponieważ zwiększa wykrywalność funkcji. Badając hierarchię przestrzeni nazw, odbiorcy biblioteki powinni mieć możliwość lokalizowania typów, które implementują funkcję.

> [!NOTE]
> Typy i uprawnienia czasu projektowania nie powinny być scalane z innymi przestrzeniami nazw w celu zachowania zgodności z tymi wskazówkami. Te typy należą do ich własnych przestrzeni nazw poniżej głównej przestrzeni nazw, a przestrzenie nazw powinny `.Design` kończyć `.Permissions`się odpowiednio i.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, spróbuj połączyć przestrzenie nazw zawierające kilka typów w pojedynczej przestrzeni nazw.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli przestrzeń nazw nie zawiera typów, które są używane z typami w innych przestrzeniach nazw, można bezpiecznie pominąć ostrzeżenie z tej reguły.