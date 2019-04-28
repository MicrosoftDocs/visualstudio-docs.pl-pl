---
title: 'CA2232: Punkty wejścia znacznik Windows Forms za pomocą atrybutu STAThread | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6e8b7242fcd82db1a0cfb82cf6cd6df5a9f75084
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435416"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nie trzeba oznaczyć projektów używających struktury aplikacji **Main** metody za pomocą atrybutu STAThread. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Kompilatora zrobi to automatycznie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy dodać <xref:System.STAThreadAttribute> atrybutu do punktu wejścia. Jeśli <xref:System.MTAThreadAttribute?displayProperty=fullName> atrybut był obecny, usuń ją.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, jeśli tworzysz dla platformy .NET Compact Framework, dla którego można bezpiecznie <xref:System.STAThreadAttribute> atrybut jest niepotrzebne i nie jest obsługiwana.

## <a name="example"></a>Przykład
 Poniższe przykłady pokazują poprawne użycie <xref:System.STAThreadAttribute>.

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
