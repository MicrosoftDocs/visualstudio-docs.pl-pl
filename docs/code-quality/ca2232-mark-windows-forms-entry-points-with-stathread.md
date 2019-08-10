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
ms.openlocfilehash: dd3f5b76015a3a54ee085b5cc2dd532920ff0795
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920176"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez przerywania|

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