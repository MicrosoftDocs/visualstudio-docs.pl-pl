---
title: 'Instrukcje: Uruchamianie programu Spy + + | Microsoft Docs'
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70874d70dd5f845e7b627f2aeb7ae51bafe45995
ms.sourcegitcommit: 7b07e7b5e06e2e13f622445c568b78a284e1a40d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542623"
---
# <a name="how-to-start-spy"></a>Porady: korzystanie z programu Spy++

Program Spy + + można uruchomić w programie Visual Studio lub w wierszu polecenia.

 Gdy uruchamiasz program Spy + +, jeśli zostanie wyświetlony komunikat z monitem o wprowadzenie zmian na komputerze, wybierz pozycję **tak**.

> [!NOTE]
> Można uruchomić tylko jedno wystąpienie programu Spy + +. Jeśli spróbujesz uruchomić drugie wystąpienie, spowoduje to jedynie, że aktualnie uruchomione wystąpienie zacznie fokus.

## <a name="prerequisites"></a>Wymagania wstępne

W programie Spy + + wymagane są następujące składniki. Można wybrać te składniki z Instalator programu Visual Studio, wybierając kartę **poszczególne składniki** , a następnie wybierając następujące składniki.

* W obszarze Debugowanie i testowanie wybierz pozycję  **C++ narzędzia profilowania**
* W obszarze działania deweloperskie wybierz pozycję  **C++ funkcje podstawowe**

Jeśli wprowadzono jakiekolwiek zmiany, postępuj zgodnie z monitami, aby zainstalować te składniki.

## <a name="start-spy-from-visual-studio"></a>Uruchom program Spy + + w programie Visual Studio

W menu **Narzędzia** wybierz polecenie **Spy + +** .

Ponieważ program Spy + + działa niezależnie, po jego uruchomieniu można zamknąć Visual Studio.

> [!NOTE]
> W przypadku rejestrowania komunikatów w programie Spy + + może dojść do spowolnienia działania systemu operacyjnego.

## <a name="start-spy-at-a-command-prompt"></a>Uruchom Spy + + w wierszu polecenia

1. W oknie wiersza polecenia Zmień katalog na folder, który zawiera spyxx. exe. Zwykle ścieżka do tego folderu to..\\\\\Common7\Tools *folderu instalacyjnego programu Visual Studio*.

2. Wprowadź **spyxx. exe**.

## <a name="see-also"></a>Zobacz także
- [Korzystanie z programu Spy++](../debugger/using-spy-increment.md)
- [Widoki w programie Spy++](../debugger/spy-increment-views.md)
- [Spy++ — dokumentacja](../debugger/spy-increment-reference.md)
