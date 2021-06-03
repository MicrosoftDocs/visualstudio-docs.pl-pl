---
title: Usuwanie nieużywanych odwołań
description: Dowiedz się, jak wyczyścić odwołania do projektu i pakiety NuGet, które nie są używane, za pomocą nowego polecenia Usuń nieużywane odwołania.
ms.custom: SEO-VS-2021
ms.date: 06/01/2021
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 707769229ad7bc1864a135bade1df918d4b27847
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2021
ms.locfileid: "111352095"
---
# <a name="remove-unused-references"></a>Usuń nieużywane odwołania

Ta refaktoryzacja ma zastosowanie do:

- C#
- Visual Basic

**Co:** Umożliwia usunięcie nieużywanych odwołań.

**Kiedy:** Chcesz wyczyścić odwołania do projektu i pakiety NuGet, które nie mają użycia. 

**Dlaczego:** Usunięcie odwołań do projektu, które nie mają użycia, może pomóc zaoszczędzić miejsce i skrócić czas uruchamiania aplikacji, ponieważ ładowanie każdego modułu zajmuje trochę czasu i pozwala uniknąć metadanych ładowania kompilatora, które nigdy nie będą używane.

## <a name="how-to"></a>Porady

1. Kliknij prawym przyciskiem myszy nazwę projektu lub węzeł zależności w Eksplorator rozwiązań.

2. Wybierz **pozycję Usuń nieużywane odwołania.**

    ![Polecenie Usuń nieużywane odwołania](media/remove-unused-references-command.png)

3. Zostanie **otwarte okno dialogowe Usuwanie nieużywanych** odwołań z wyświetlonymi odwołaniami, które nie mają użycia w kodzie źródłowym. Nieużywane odwołania zostaną wstępnie wybrane do usunięcia z opcją zachowania odwołań przez wybranie z `Keep` listy rozwijanej Akcja.

    ![Okno dialogowe Usuń nieużywane odwołania](media/remove-unused-references-dialog.png)

5. Kliknij, `Apply` aby usunąć wybrane odwołania. 

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)