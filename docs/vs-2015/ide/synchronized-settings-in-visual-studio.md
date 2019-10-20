---
title: Zsynchronizowane ustawienia
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6459b6f65fd1e29fbadb01f6aa2fc51520b726b8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646825"
---
# <a name="synchronized-settings-in-visual-studio"></a>Synchronizacja ustawień w Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli używasz tego samego konta personalizacji do logowania się do programu Visual Studio na wielu komputerach, domyślnie ustawienia są synchronizowane na wszystkich komputerach.

## <a name="synchronized-settings"></a>Zsynchronizowane ustawienia
 Domyślnie synchronizowane są następujące ustawienia.

- Ustawienia deweloperskie (należy wybrać zestaw ustawień przy pierwszym uruchomieniu programu Visual Studio, ale można zmienić zaznaczenie w dowolnym momencie. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

- Następujące opcje na stronach **Opcje narzędzi &#124;**  :

  - **Motyw** i pasek menu ustawienia wielkości liter, na stronie **środowisko**, **Ogólne** opcje

  - Wszystkie ustawienia na stronie opcje **środowiska**, **czcionek i kolorów**

  - Wszystkie skróty klawiaturowe na stronie **środowisko**, opcje **klawiatury**

  - Wszystkie ustawienia na stronie **środowisko, karty i opcje systemu Windows**

  - Wszystkie ustawienia w **środowisku**, na stronie opcje **uruchamiania**

  - Wszystkie ustawienia na stronach opcji **edytora tekstu**

- Wszystkie ustawienia na stronach opcji projektant XAML

- Aliasy poleceń zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji o definiowaniu aliasów poleceń, zobacz [Visual Studio — Aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).

- Układy okien zdefiniowane przez użytkownika w **oknie &#124; zarządzanie układami** okien

## <a name="turning-synchronized-settings-off-for-a-particular-computer"></a>Wyłączanie synchronizacji ustawień dla określonego komputera
 Zsynchronizowane ustawienia dla programu Visual Studio są domyślnie włączone. Zsynchronizowane ustawienia można wyłączyć na komputerze, przechodząc do strony **Opcje &#124; &#124; narzędzi Synchronizuj ustawienia &#124; środowiska** , a następnie usuwając zaznaczenie pola wyboru.  Na przykład jeśli zdecydujesz, że nie chcesz synchronizować ustawień programu Visual Studio na komputerze A, wszelkie zmiany ustawień wprowadzone na komputerze A nie pojawiają się na komputerze B lub na komputerze C. komputer B i C będzie nadal synchronizować się ze sobą, ale nie z komputerem A.

## <a name="synchronizing-settings-across-visual-studio-family-products-and-editions"></a>Synchronizowanie ustawień w produktach i wersjach rodziny Visual Studio
 Ustawienia można synchronizować w dowolnej wersji programu Visual Studio 2015, w tym wersji Express i Community. Ustawienia są również synchronizowane między produktami rodziny Visual Studio, takimi jak Blend. Jednak każdy z tych produktów rodziny może mieć własne ustawienia, które nie są udostępniane w programie Visual Studio. Na przykład ustawienia specyficzne dla programu Blend na komputerze A będą współużytkowane z programem Blend na komputerze B, ale nie z programem Visual Studio na komputerze A lub B.

> [!WARNING]
> Ustawienia nie są zsynchronizowane między Visual Studio 2013 i Visual Studio 2015. Przy pierwszym otwarciu programu Visual Studio 2015 ustawienia z Visual Studio 2013 są migrowane, ale nie można ich migrować z powrotem do Visual Studio 2013 po tym.

## <a name="see-also"></a>Zobacz też
 [Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)
