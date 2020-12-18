---
title: Zmień klawisz pomocy F1
description: Opisuje, jak ponownie mapować lub usunąć mapowanie klawisza F1
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
robots: noindex,nofollow
manager: jillfra
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: d9add6996949a97d6140ab6d063f13e02b677e79
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684077"
---
# <a name="change-the-f1-help-key-in-visual-studio"></a>Zmiana klawisza pomocy F1 w programie Visual Studio

Jeśli chcesz użyć klawisza F1 dla innej funkcji niż usługa pomocy F1 lub po prostu chcesz wyłączyć pomoc przy użyciu klawisza F1, możesz usunąć lub zmodyfikować mapowanie klucza.

> [!IMPORTANT]
> Jeśli chcesz wyłączyć Pomoc F1 ze względu na problemy z wydajnością, zalecamy tymczasowe modyfikowanie mapowania kluczy, aby umożliwić przetestowanie ulepszeń usługi pomocy F1 w aktualizacjach programu Visual Studio. W większości scenariuszy F1 jest łatwym sposobem otwierania stron odniesienia dla słów kluczowych języka i interfejsów API z edytora kodu lub do otwierania stron pomocy skojarzonych z oknami lub elementami interfejsu użytkownika w IDE. Jeśli wyłączysz ją, wyłączysz ją w celu użycia w programie Visual Studio.

**Aby wyłączyć Pomoc F1:**

1. W programie Visual Studio wybierz pozycję **Narzędzia**  >  **Opcje**, a następnie w obszarze **środowisko** wybierz pozycję **Klawiatura**.

1. W polu tekstowym **Pokaż polecenia zawierające** wpisz **help. F1** , aby odfiltrować widok poleceń.

   ![Wyłącz Pomoc F1](../not-in-toc/media/disable-f1-help-key.png)

1. Wybierz pozycję **Usuń** , aby usunąć mapowanie klucza.

1. Zaznacz pole tekstowe **naciśnij klawisz skrótu** .

1. Na klawiaturze naciśnij nowy klawisz lub kombinację klawiszy dla pomocy F1, na przykład **ALT + F1**, wybierz pozycję **Assign**, a następnie wybierz przycisk **OK**.

Aby uzyskać więcej informacji na temat ustawiania skrótów klawiaturowych, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
