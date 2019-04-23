---
title: 'Instrukcje: Pluralizacja Włączanie i wyłączanie (Projektant O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 34b25be50cee681ee9c45e446d86a6054099926b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103748"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Instrukcje: Pluralizacja Włączanie i wyłączanie (O/R Designer)
Domyślnie podczas przeciągania obiektów bazy danych, które mają nazwy kończące się na s lub ię od **Eksploratora serwera** lub **Eksplorator bazy danych** na [LINQ to SQL tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), nazwy wygenerowanych klas jednostek nie zostaną zmienione w liczbie mnogiej na liczbę pojedynczą. W ten sposób bardziej przedstawiać fakt, że klasa wystąpień jednostki mapowany na pojedynczy rekord danych. Na przykład dodanie `Customers` do tabeli **O/R Designer** skutkuje klasę jednostki o nazwie `Customer` ponieważ klasa przechowuje dane dla jednego klienta.

> [!NOTE]
>  Pluralizacja jest domyślnie tylko w języku angielskim wersji programu Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Aby włączyć pluralizacja włączać i wyłączać

1. Na **narzędzia** menu, kliknij przycisk **opcje**.

2. W **opcje** okna dialogowego rozwiń **narzędzia graficzne bazy danych**.

    > [!NOTE]
    >  Wybierz **Pokaż wszystkie ustawienia** Jeśli **narzędzia graficzne bazy danych** węzeł nie jest widoczny.

3. Kliknij przycisk **O/R Designer**.

4. Ustaw **Pluralizację nazw** do **włączone** = **False** można ustawić **O/R Designer** tak, aby nie zmienia nazwy klas .

5. Ustaw **Pluralizację nazw** do **włączone** = **True** mają dotyczyć zasady pluralizacja nazw klasy obiekty dodane do **O/R Projektant**.

## <a name="see-also"></a>Zobacz także

- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)