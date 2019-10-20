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
ms.openlocfilehash: 084e7a093f92aa8eda9d9edc11865ac319adfad0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662794"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Oznacz punkty wpisu formularzy systemu Windows za pomocą STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Zestaw odwołuje się do przestrzeni nazw <xref:System.Windows.Forms>, a jego punkt wejścia nie jest oznaczony atrybutem <xref:System.STAThreadAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 <xref:System.STAThreadAttribute> wskazuje, że model wątkowości COM dla aplikacji jest apartamentem jednowątkowym. Atrybut ten musi być obecny w punkcie wejścia każdej aplikacji korzystającej z Windows Forms; jeśli zostanie pominięty, składniki systemu Windows mogą nie działać poprawnie. Jeśli atrybut nie jest obecny, aplikacja używa wielowątkowego modelu apartamentu, który nie jest obsługiwany przez Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty, które używają struktury aplikacji, nie muszą oznaczać metody **Main** z STAThread. Kompilator [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] wykonuje automatyczne.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj atrybut <xref:System.STAThreadAttribute> do punktu wejścia. Jeśli atrybut <xref:System.MTAThreadAttribute?displayProperty=fullName> jest obecny, usuń go.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 W przypadku opracowywania .NET Compact Framework, dla którego atrybut <xref:System.STAThreadAttribute> jest zbędny i nie jest obsługiwany, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 W poniższych przykładach pokazano poprawne użycie <xref:System.STAThreadAttribute>.

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
