---
title: 'CA2232: Oznacz punkty wejścia Windows Forms za pomocą STAThread | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 42bb554f8e57c036d41a89fdc2657a25ecc74e20
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540286"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Zestaw odwołuje się do <xref:System.Windows.Forms> przestrzeni nazw, a jego punkt wejścia nie jest oznaczony <xref:System.STAThreadAttribute?displayProperty=fullName> atrybutem.

## <a name="rule-description"></a>Opis reguły
 <xref:System.STAThreadAttribute>wskazuje, że model wątkowości COM dla aplikacji jest apartamentem jednowątkowym. Atrybut ten musi być obecny w punkcie wejścia każdej aplikacji korzystającej z Windows Forms; jeśli zostanie pominięty, składniki systemu Windows mogą nie działać poprawnie. Jeśli atrybut nie jest obecny, aplikacja używa wielowątkowego modelu apartamentu, który nie jest obsługiwany przez Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]projekty korzystające ze struktury aplikacji nie muszą oznaczać metody **Main** z STAThread. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]Kompilator robi automatycznie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj <xref:System.STAThreadAttribute> atrybut do punktu wejścia. Jeśli <xref:System.MTAThreadAttribute?displayProperty=fullName> atrybut jest obecny, usuń go.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli tworzysz .NET Compact Framework, dla którego <xref:System.STAThreadAttribute> atrybut jest zbędny i nie jest obsługiwany, bezpieczniej jest pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 W poniższych przykładach pokazano poprawne użycie programu <xref:System.STAThreadAttribute> .

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
