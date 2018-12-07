---
title: Zsynchronizowane ustawienia
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1b0ab4b0d006183f6be3c42626c022d45a2de4ce
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067132"
---
# <a name="synchronized-settings-in-visual-studio"></a>Synchronizacja ustawień w Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Korzystając z tego samego konta personalizacji zalogować się do programu Visual Studio na wielu komputerach, ustawienia są domyślnie synchronizowane na wszystkich komputerach.

## <a name="synchronized-settings"></a>Zsynchronizowane ustawienia
 Domyślnie zsynchronizowane są następujące ustawienia.

-   Ustawienia środowiska deweloperskiego (musisz wybrać zestaw ustawień przy pierwszym uruchomieniu programu Visual Studio, ale możesz zmienić wybór w dowolnym momencie. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).)

-   Następujące opcje w **narzędzia &#124; opcje** strony:

    -   **Motyw** i pasek wielkość liter ustawienia, w menu **środowiska**, **ogólne** strony opcji

    -   Wszystkie ustawienia na **środowiska**, **czcionki i kolory** strony opcji

    -   Wszystkie skróty klawiaturowe, na **środowiska**, **klawiatury** strony opcji

    -   Wszystkie ustawienia na **środowiska, karty i Windows** strony opcji

    -   Wszystkie ustawienia na **środowiska**, **uruchamiania** strony opcji

    -   Wszystkie ustawienia na **edytora tekstów** Opcje strony

-   Wszystkie ustawienia w Projektancie XAML Opcje strony

-   Aliasy zdefiniowane przez użytkownika polecenia. Aby uzyskać więcej informacji o definiowaniu aliasów poleceń, zobacz [Visual Studio — aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).

-   Układów okien zdefiniowanych przez użytkownika w **okna &#124; Zarządzanie układami okien** strony

## <a name="turning-synchronized-settings-off-for-a-particular-computer"></a>Włączanie synchronizacji ustawień, wyłączyć dla określonego komputera
 Synchronizacja ustawień dla programu Visual Studio są włączone domyślnie. Zsynchronizowane ustawienia na komputerze, można wyłączyć, przechodząc do **narzędzia &#124; opcje &#124; środowiska &#124; zsynchronizowane ustawienia** strony i usuwając zaznaczenie pola wyboru.  Na przykład, jeśli nie chcesz synchronizować ustawienia programu Visual Studio na komputerze A, zmiany ustawień wprowadzone na komputerze czy, nie pojawiają się na komputerze B lub komputerze C. komputerze B i C, będą nadal do synchronizacji ze sobą, ale nie z komputera A.

## <a name="synchronizing-settings-across-visual-studio-family-products-and-editions"></a>Synchronizacja ustawień przez wersje i rodziny produktów Visual Studio
 Ustawienia mogą być synchronizowane w dowolnej wersji programu Visual Studio 2015, łącznie z wersji Express i społeczności. Ustawienia są synchronizowane między rodziny produktów Visual Studio, takich jak Blend. Jednak każdy z tych produktów z rodziny mogą mieć własne ustawienia, które nie są współdzielone z programem Visual Studio. Na przykład udostępniane ustawienia specyficzne dla programu Blend, na komputerze A przy użyciu programu Blend, na komputerze B, ale nie za pomocą programu Visual Studio na komputerze A i B.

> [!WARNING]
>  Ustawienia nie są zsynchronizowane między Visual Studio 2013 i Visual Studio 2015. Przy pierwszym otwarciu programu Visual Studio 2015, ustawienia usługi z programu Visual Studio 2013 są migrowane, ale nie mogą być migrowane do programu Visual Studio 2013 po tym.

## <a name="see-also"></a>Zobacz też
 [Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)
