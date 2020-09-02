---
title: 'Instrukcje: Włączanie i wyłączanie pluralizacja (Projektant O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: afe8c8a4429efb83c09d80a5dd00dfe08b0d63e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665935"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Instrukcje: włączanie i wyłączanie pluralizacji (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie, gdy przeciągasz obiekty bazy danych, które mają nazwy kończące się na s lub z **Eksplorator serwera** / **Eksplorator bazy danych** do [narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), nazwy wygenerowanych klas jednostek są zmieniane z plural na liczbę pojedynczą. Jest to bardziej dokładne przedstawienie faktu, że Klasa jednostki wystąpienia jest mapowana na pojedynczy rekord danych. Na przykład dodanie tabeli Customers do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] wyników w klasie jednostki o nazwie klient, ponieważ klasa będzie przechowywać dane tylko dla jednego klienta.

> [!NOTE]
> Pluralizacja jest domyślnie włączona tylko w angielskiej wersji językowej programu Visual Studio.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Aby włączyć i wyłączyć pluralizacja

1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

2. W oknie dialogowym **Opcje** rozwiń węzeł **Narzędzia bazy danych**.

> [!NOTE]
> Wybierz opcję **Pokaż wszystkie ustawienia** , jeśli węzeł **Narzędzia bazy danych** nie jest widoczny.

1. Kliknij przycisk **projektanta O/R**.

2. Ustaw **pluralizacja nazw** **na**  =  **wartość false** , aby ustawić, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tak aby nie zmieniać nazw klas.

3. Ustaw **pluralizacja nazw** **na**  =  **wartość true** , aby zastosować reguły pluralizacja do nazw klas obiektów dodanych do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

## <a name="see-also"></a>Zobacz też
 [Narzędzia LINQ to SQL w programie Visual studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [uzyskiwania dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
