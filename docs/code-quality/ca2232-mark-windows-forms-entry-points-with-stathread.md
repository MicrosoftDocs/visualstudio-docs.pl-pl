---
title: 'CA2232: Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 06772f8dd91c27834b329293d06cfbc2a7dcfcef
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230758"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Zestaw odwołuje się <xref:System.Windows.Forms> do przestrzeni nazw, a jego punkt wejścia nie jest oznaczony <xref:System.STAThreadAttribute?displayProperty=fullName> atrybutem.

## <a name="rule-description"></a>Opis reguły
 <xref:System.STAThreadAttribute>wskazuje, że model wątkowości COM dla aplikacji jest apartamentem jednowątkowym. Atrybut ten musi być obecny w punkcie wejścia każdej aplikacji korzystającej z Windows Forms; jeśli zostanie pominięty, składniki systemu Windows mogą nie działać poprawnie. Jeśli atrybut nie jest obecny, aplikacja używa wielowątkowego modelu apartamentu, który nie jest obsługiwany przez Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]projekty korzystające ze struktury aplikacji nie muszą oznaczać metody **Main** z STAThread. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Kompilator robi automatycznie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Dodaj <xref:System.STAThreadAttribute> atrybut do punktu wejścia. <xref:System.MTAThreadAttribute?displayProperty=fullName> Jeśli atrybut jest obecny, usuń go.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli tworzysz .NET Compact Framework, dla którego <xref:System.STAThreadAttribute> atrybut jest zbędny i nie jest obsługiwany, bezpieczniej jest pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
W poniższych przykładach pokazano poprawne użycie <xref:System.STAThreadAttribute>:

[!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
[!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]