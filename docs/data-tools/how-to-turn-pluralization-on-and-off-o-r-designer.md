---
title: 'Instrukcje: Włączanie i wyłączanie pluralizacja (Projektant O-R)'
description: Dowiedz się, jak włączać i wyłączać pluralizacja w Object Relational Designer (Projektant O/R). Ustawienie domyślne konwertuje nazwy w liczbie mnogiej na liczbę pojedynczą.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 609af4ef71a6ed73bd1d9599d76d8eb64073efd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858699"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Instrukcje: włączanie i wyłączanie pluralizacji (O/R Designer)
Domyślnie, gdy przeciągasz obiekty bazy danych, które mają nazwy kończące się na s lub z **Eksplorator serwera** lub **Eksplorator bazy danych** do [narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), nazwy wygenerowanych klas jednostek są zmieniane z plural na liczbę pojedynczą. Jest to bardziej dokładne przedstawienie faktu, że Klasa jednostki wystąpienia jest mapowana na pojedynczy rekord danych. Na przykład dodanie `Customers` tabeli do **projektanta O/R** powoduje wystąpienie klasy jednostki o nazwie `Customer` , ponieważ klasa będzie przechowywać dane tylko dla jednego klienta.

> [!NOTE]
> Pluralizacja jest domyślnie włączona tylko w angielskiej wersji językowej programu Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Aby włączyć i wyłączyć pluralizacja

1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

2. W oknie dialogowym **Opcje** rozwiń węzeł **Narzędzia bazy danych**.

    > [!NOTE]
    > Wybierz opcję **Pokaż wszystkie ustawienia** , jeśli węzeł **Narzędzia bazy danych** nie jest widoczny.

3. Kliknij przycisk **projektanta O/R**.

4. Ustaw **pluralizacja nazw** **na**  =  **wartość false** , aby ustawić **projektanta O/R** tak, aby nie zmieniać nazw klas.

5. Ustaw **pluralizacja nazw** **na**  =  **wartość true** , aby zastosować reguły pluralizacja do nazw klas obiektów dodanych do **projektanta O/R**.

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
