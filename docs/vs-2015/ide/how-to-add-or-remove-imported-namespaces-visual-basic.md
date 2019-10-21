---
title: 'Instrukcje: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 75299dae66a07b2bc1671dbfcda935fc4af2b284
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645500"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Porady: dodawanie i usuwanie importowanych przestrzeni nazw (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Importowanie przestrzeni nazw pozwala używać elementów z tej przestrzeni nazw w kodzie bez w pełni zakwalifikowania elementu. Na przykład jeśli chcesz uzyskać dostęp do metody `Create` w klasie `System.Messaging.MessageQueue`, możesz zaimportować przestrzeń nazw `System.Messaging` i po prostu odwołać się do elementu, którego potrzebujesz w kodzie jako `MessageQueue.Create`.

 Importowane przestrzenie nazw są zarządzane na stronie **odwołania** **projektanta projektu**. Importy określone w tym oknie dialogowym są przesyłane bezpośrednio do kompilatora (`/imports`) i stosowane do wszystkich plików w projekcie. Użyj instrukcji `Imports`, aby użyć przestrzeni nazw w jednym pliku kodu źródłowego.

### <a name="to-add-an-imported-namespace"></a>Aby dodać zaimportowaną przestrzeń nazw

1. W **Eksplorator rozwiązań**kliknij dwukrotnie węzeł **mój projekt** dla projektu.

2. W **projektancie projektu**kliknij kartę **odwołania** .

3. Na liście **zaimportowanych obszarów nazw** zaznacz pole wyboru dla przestrzeni nazw, którą chcesz dodać.

    > [!NOTE]
    > W celu zaimportowania przestrzeń nazw musi znajdować się w składniku, do którego się odwołuje. Jeśli przestrzeń nazw nie występuje na liście, należy dodać odwołanie do składnika, który go zawiera. Aby uzyskać więcej informacji, zobacz [NIB How to: Dodawanie lub usuwanie odwołań za pomocą okna dialogowego Dodawanie odwołania](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

### <a name="to-remove-an-imported-namespace"></a>Aby usunąć zaimportowaną przestrzeń nazw

1. W **Eksplorator rozwiązań**kliknij dwukrotnie węzeł **mój projekt** dla projektu.

2. W **projektancie projektu**kliknij kartę **odwołania** .

3. Na liście **zaimportowanych obszarów nazw** Usuń zaznaczenie pola wyboru dla przestrzeni nazw, która ma zostać usunięta.

## <a name="user-imports"></a>Importy użytkowników
 Importy użytkowników umożliwiają importowanie określonej klasy w przestrzeni nazw, a nie całej przestrzeni nazw. Na przykład aplikacja może mieć import dla przestrzeni nazw `Systems.Diagnostics`, ale jedyną klasą w tej przestrzeni nazw, która Cię interesuje, jest Klasa `Debug`. Można zdefiniować `System.Diagnostics.Debug` jako import użytkownika, a następnie usunąć import dla `System.Diagnostics`.

 Jeśli później zmienisz zdanie i zdecydujesz, że było to naprawdę konieczne `EventLog` klasie, możesz wprowadzić `System.Diagnostics.EventLog` jako import i zastępować `System.Diagnostics.Debug` przy użyciu funkcji aktualizacji.

#### <a name="to-add-a-user-import"></a>Aby dodać Importowanie użytkownika

1. W **Eksplorator rozwiązań**kliknij dwukrotnie węzeł **mój projekt** dla projektu.

2. W **projektancie projektu**kliknij kartę **odwołania** .

3. W polu tekstowym pod listą **importowanych obszarów nazw** wprowadź pełną nazwę przestrzeni nazw, która ma zostać zaimportowana, w tym główną przestrzeń nazw.

4. Kliknij przycisk **Dodaj Import użytkownika** , aby dodać przestrzeń nazw do listy **importowanych obszarów nazw** .

    > [!NOTE]
    > Przycisk **Dodaj Import użytkownika** zostanie wyłączony, jeśli przestrzeń nazw pasuje do jednego z nich znajdującego się już na liście; nie można dodać importu dwa razy.

#### <a name="to-update-a-user-import"></a>Aby zaktualizować Importowanie użytkownika

1. W **Eksplorator rozwiązań**kliknij dwukrotnie węzeł **mój projekt** dla projektu.

2. W **projektancie projektu**kliknij kartę **odwołania** .

3. Z listy **zaimportowanych obszarów nazw** wybierz przestrzeń nazw, którą chcesz zmienić.

4. W polu tekstowym pod listą **importowanych obszarów** nazw wprowadź nazwę nowej przestrzeni nazw.

5. Kliknij przycisk **Aktualizuj Import użytkowników** , aby zaktualizować przestrzeń nazw na liście **zaimportowanych przestrzeni nazw** .

## <a name="see-also"></a>Zobacz też
 [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
