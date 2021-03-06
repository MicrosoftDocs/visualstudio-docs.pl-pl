---
title: Uruchom Spy + + | Microsoft Docs
description: Zapoznaj się z tematem uruchamiania narzędzia Spy + + z poziomu programu Visual Studio lub w wierszu polecenia, gdy chcesz debugować rozwiązanie.
ms.custom: SEO-VS-2020
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0e8b1125534e52c810f97c91bd00ea53dfd3d6de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896620"
---
# <a name="how-to-start-spy"></a>Porady: korzystanie z programu Spy++

Program Spy + + można uruchomić w programie Visual Studio lub w wierszu polecenia.

 Gdy uruchamiasz program Spy + +, jeśli zostanie wyświetlony komunikat z monitem o wprowadzenie zmian na komputerze, wybierz pozycję **tak**.

> [!NOTE]
> Można uruchomić tylko jedno wystąpienie programu Spy + +. Jeśli spróbujesz uruchomić drugie wystąpienie, spowoduje to jedynie, że aktualnie uruchomione wystąpienie zacznie fokus.

## <a name="prerequisites"></a>Wymagania wstępne

W programie Spy + + wymagane są następujące składniki. Można wybrać te składniki z Instalator programu Visual Studio, wybierając kartę **poszczególne składniki** , a następnie wybierając następujące składniki.

* W obszarze Debugowanie i testowanie wybierz pozycję **narzędzia profilowania języka C++**
* W obszarze działania deweloperskie wybierz pozycję **podstawowe funkcje języka C++**

Jeśli wprowadzono jakiekolwiek zmiany, postępuj zgodnie z monitami, aby zainstalować te składniki.

## <a name="start-spy-from-visual-studio"></a>Uruchom program Spy + + w programie Visual Studio

W menu **Narzędzia** wybierz polecenie **Spy + +**.

Ponieważ program Spy + + działa niezależnie, po jego uruchomieniu można zamknąć Visual Studio.

> [!NOTE]
> W przypadku rejestrowania komunikatów w programie Spy + + może dojść do spowolnienia działania systemu operacyjnego.

## <a name="start-spy-at-a-command-prompt"></a>Uruchom Spy + + w wierszu polecenia

1. W oknie wiersza polecenia Zmień katalog na folder, który zawiera spyxx.exe. Zwykle ścieżka do tego folderu to.. \\ *Folder instalacyjny programu Visual Studio*\Common7\Tools \\ .

2. Wprowadź **spyxx.exe**.

## <a name="see-also"></a>Zobacz też
- [Korzystanie z programu Spy++](../debugger/using-spy-increment.md)
- [Spy++ — Widoki](../debugger/spy-increment-views.md)
- [Spy++ — Odwołanie](../debugger/spy-increment-reference.md)
