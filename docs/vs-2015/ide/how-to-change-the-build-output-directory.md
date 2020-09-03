---
title: 'Instrukcje: zmiana katalogu wyjściowego kompilacji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b665f5788d12c294e8ab7f55ecc63d183030a0ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645431"
---
# <a name="how-to-change-the-build-output-directory"></a>Porady: zmiana budowy katalogu wyjściowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz określić lokalizację danych wyjściowych dla poszczególnych konfiguracji (dla debugowania, wydania lub obu), które zostały wygenerowane przez projekt.

> [!NOTE]
> Jeśli masz projekt **konfiguracji** , zapoznaj się z uwagą na końcu tego artykułu.

## <a name="changing-the-build-output-directory"></a>Zmiana katalogu wyjściowego kompilacji

#### <a name="to-change-the-build-output-directory"></a>Aby zmienić katalog wyjściowy kompilacji

1. Na pasku menu wybierz **projekt**, **Właściwości** *nazwa_aplikacji* . Możesz również kliknąć prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybrać polecenie **Właściwości**.

2. Jeśli masz projekt Visual Basic, wybierz kartę **kompilacja** . Jeśli masz projekt Visual C#, wybierz kartę **kompilacja** . Jeśli masz projekt C++ lub projekt JavaScript, wybierz kartę **Ogólne** .

3. Na liście rozwijanej konfiguracja u góry wybierz konfigurację, której lokalizację pliku wyjściowego chcesz zmienić (debugowanie, wydanie lub wszystkie).

     Znajdź wpis ścieżki wyjściowej (**Ścieżka wyjściowa kompilacji** w Visual Basic, **katalog wyjściowy** w Visual C++, **Ścieżka wyjściowa** w języku JavaScript i C#). Określ nowy katalog wyjściowy kompilacji względem katalogu projektu.

> [!NOTE]
> W projekcie instalacyjnym pole **Nazwa pliku wyjściowego** zmienia tylko lokalizację pliku Setup.exe, a nie lokalizację plików projektu. Aby uzyskać więcej informacji, zobacz **kompilacja, właściwości konfiguracji, okno dialogowe właściwości projektu wdrożenia**.

## <a name="see-also"></a>Zobacz też
 [Strona kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md) [ogólna Strona właściwości (projekt)](https://msdn.microsoft.com/library/593b383c-cd0f-4dcd-ad65-9ec9b4b19c45) [Kompilowanie i kompilowanie](../ide/compiling-and-building-in-visual-studio.md)
