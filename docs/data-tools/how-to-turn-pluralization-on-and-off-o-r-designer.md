---
title: 'Instrukcje: Włączanie i wyłączanie pluralizacja (Projektant O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 54b3376f9388116f179e2b09bcd136a37f3029f5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586448"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Instrukcje: Włączanie i wyłączanie pluralizacja (Projektant O/R)
Domyślnie, gdy przeciągasz obiekty bazy danych, które mają nazwy kończące się na s lub z **Eksplorator serwera** lub **Eksplorator bazy danych** do [narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), nazwy wygenerowanych klas jednostek są zmieniane z plural na liczbę pojedynczą. Jest to bardziej dokładne przedstawienie faktu, że Klasa jednostki wystąpienia jest mapowana na pojedynczy rekord danych. Na przykład dodanie tabeli `Customers` do **projektanta O/R** skutkuje wynikiem klasy jednostki o nazwie `Customer`, ponieważ klasa będzie przechowywać dane tylko dla jednego klienta.

> [!NOTE]
> Pluralizacja jest domyślnie włączona tylko w angielskiej wersji językowej programu Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Aby włączyć i wyłączyć pluralizacja

1. Na **narzędzia** menu, kliknij przycisk **opcje**.

2. W oknie dialogowym **Opcje** rozwiń węzeł **Narzędzia bazy danych**.

    > [!NOTE]
    > Wybierz opcję **Pokaż wszystkie ustawienia** , jeśli węzeł **Narzędzia bazy danych** nie jest widoczny.

3. Kliknij przycisk **projektanta O/R**.

4. Ustaw **pluralizacja nazw** , które mają być **włączone** = **false** , aby ustawić **projektanta O/R** tak, aby nie zmieniać nazw klas.

5. Ustaw **pluralizacja nazw** , które mają być **włączone** = **true** , aby zastosować reguły pluralizacja do nazw klas obiektów dodanych do **projektanta O/R**.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
