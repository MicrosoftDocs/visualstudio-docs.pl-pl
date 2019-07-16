---
title: Pole wyszukiwania polecenia | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b8bddc27eb4a59b65796c7837ae4561e5d56a5d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160678"
---
# <a name="findcommand-box"></a>Find/Command — Pole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można wyszukać tekst i uruchomić polecenia programu Visual Studio z **Find/Command** pole. **Find/Command** pole jest nadal dostępne jako formant paska narzędzi, ale nie jest już domyślnie widoczne. Możesz wyświetlić **Find/Command** pola, wybierając **apletu Dodaj lub usuń przyciski** na **standardowa** narzędzi, a następnie wybierając **znaleźć**.  
  
 Aby uruchomić [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] polecenia, należy poprzedzić go znakiem większe niż (>).  
  
 **Find/Command** pole zachowa ostatnie 20 elementów, które wprowadzono i wyświetla je na liście rozwijanej. Możesz przejść przez listę, wybierając klawisze strzałek.  
  
 ![Znajdź&#47;polecenia pole](../ide/media/findcommandbox.png "FindCommandBox")  
Find/Command — Pole  
  
## <a name="searching-for-text"></a>Wyszukiwanie tekstu  
 Domyślnie, gdy Określ tekst w **Find/Command** pole, a następnie wybierz ENTER klucza, Visual Studio wyszukuje bieżące okno narzędzia lub dokumentu, korzystając z opcji, które są określone w **Znajdź w plikach**okno dialogowe. Aby uzyskać więcej informacji, zobacz [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md).  
  
## <a name="entering-commands"></a>Wprowadzenie poleceń  
 Do użycia **Find/Command** pole, aby wystawić pojedynczej [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] polecenie lub alias zamiast wyszukiwania tekstu, należy wprowadzić [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] polecenia poprzedzone znakiem symbol większe niż (>). Przykład:  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 Alternatywnie umożliwia także z okna poleceń do wprowadzania i wykonywanie jednego lub wielu poleceń. Wprowadzony i wykonywane przez siebie; niektórych poleceń ani aliasów masz inne wymagane argumenty w składni. Aby uzyskać listę poleceń, które ma argumentów, zobacz [polecenia programu Visual Studio](../ide/reference/visual-studio-commands.md).  
  
## <a name="escape-characters"></a>Znaki specjalne  
 W wierszu polecenia znak karetki (^) oznacza, że znak natychmiast po jego jest interpretowany dosłownie, a nie jako znak kontrolny. Może to służyć do osadzania prostych znaków cudzysłowu ("), spacji, ukośników wiodących, daszków lub innych znaków literałowych w wartości parametru lub przełącznika, z wyjątkiem nazw przełączników. Na przykład  
  
```  
>Edit.Find ^^t /regex  
```  
  
 Daszek działa tak samo, czy wewnątrz lub poza znaki cudzysłowu. Jeśli znak daszka jest ostatnim znakiem w wierszu, jest on ignorowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Okno polecenia](../ide/reference/command-window.md)   
 [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)
