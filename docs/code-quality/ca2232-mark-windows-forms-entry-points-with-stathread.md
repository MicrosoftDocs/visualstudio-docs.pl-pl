---
title: 'CA2232: Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 1ee37645d1cc20bfd83a18b9dbb7a001731702f1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043677"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Odwołuje się zestaw <xref:System.Windows.Forms> przestrzeni nazw i jego punktu wejścia nie jest oznaczony atrybutem <xref:System.STAThreadAttribute?displayProperty=fullName> atrybutu.

## <a name="rule-description"></a>Opis reguły
 <xref:System.STAThreadAttribute> Wskazuje, że model wątkowości COM dla aplikacji jest jednowątkowym apartamentem. Atrybut ten musi być obecny w punkcie wejścia każdej aplikacji korzystającej z Windows Forms; jeśli zostanie pominięty, składniki systemu Windows mogą nie działać poprawnie. Jeśli ten atrybut nie jest obecny, aplikacja korzysta z modelu apartamentu wielowątkowych, który nie jest obsługiwana dla formularzy Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nie trzeba oznaczyć projektów używających struktury aplikacji **Main** metody za pomocą atrybutu STAThread. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Kompilatora zrobi to automatycznie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy dodać <xref:System.STAThreadAttribute> atrybutu do punktu wejścia. Jeśli <xref:System.MTAThreadAttribute?displayProperty=fullName> atrybut był obecny, usuń ją.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, jeśli tworzysz dla platformy .NET Compact Framework, dla którego można bezpiecznie <xref:System.STAThreadAttribute> atrybut jest niepotrzebne i nie jest obsługiwana.

## <a name="example"></a>Przykład
 Poniższe przykłady pokazują poprawne użycie <xref:System.STAThreadAttribute>:

 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]