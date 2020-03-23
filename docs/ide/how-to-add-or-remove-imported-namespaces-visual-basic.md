---
title: 'Jak: Dodawanie lub usuwanie importowanych obszarów nazw (Visual Basic)'
ms.date: 06/21/2017
ms.topic: conceptual
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e636969164c4cf2526bb85add95e7cfe02ce6176
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593333"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Jak: Dodawanie lub usuwanie importowanych obszarów nazw (Visual Basic)

Importowanie obszaru nazw umożliwia użycie elementów z tego obszaru nazw w kodzie bez pełnego kwalifikowania elementu. Na przykład, jeśli chcesz `Create` uzyskać dostęp `System.Messaging.MessageQueue` do metody w `System.Messaging` klasie, możesz zaimportować obszar `MessageQueue.Create`nazw i po prostu odwołać się do elementu, którego potrzebujesz w kodzie jako .

Importowane przestrzenie nazw są zarządzane na stronie **Odwołania** **projektanta projektu**. Importy określone w tym oknie dialogowym są przekazywane bezpośrednio do kompilatora (*/imports*) i dotyczą wszystkich plików w projekcie. Instrukcja `Imports` służy do używania obszaru nazw w jednym pliku kodu źródłowego.

### <a name="to-add-an-imported-namespace"></a>Aby dodać zaimportowany obszar nazw

1. W **Eksploratorze rozwiązań**kliknij dwukrotnie węzeł **Mój projekt** dla projektu.

2. W **Projektancie projektów**kliknij kartę **Odwołania.**

3. Na liście **Importowane przestrzenie nazw** zaznacz pole wyboru obszaru nazw, który chcesz dodać.

    > [!NOTE]
    > Aby można było zaimportować, obszar nazw musi znajdować się w składniku, do którego istnieje odwołanie. Jeśli obszar nazw nie jest wyświetlany na liście, należy dodać odwołanie do składnika, który go zawiera. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](managing-references-in-a-project.md).

### <a name="to-remove-an-imported-namespace"></a>Aby usunąć zaimportowany obszar nazw

1. W **Eksploratorze rozwiązań**kliknij dwukrotnie węzeł **Mój projekt** dla projektu.

2. W **Projektancie projektów**kliknij kartę **Odwołania.**

3. Na liście **Importowane przestrzenie nazw wyczyść** pole wyboru obszaru nazw, który chcesz usunąć.

## <a name="user-imports"></a>Importy użytkowników
Importowanie przez użytkowników umożliwia importowanie określonej klasy w obszarze nazw, a nie w całym obszarze nazw. Na przykład aplikacja może mieć import <xref:System.Diagnostics> dla obszaru nazw, ale jedyną klasą w `Debug` tej przestrzeni nazw, która cię interesuje, jest klasa. Można zdefiniować <xref:System.Diagnostics.Debug> jako import użytkownika, a <xref:System.Diagnostics>następnie usunąć import dla .

Jeśli później zmienisz zdanie i zdecydujesz, że naprawdę była to `EventLog` klasa, której potrzebujesz, możesz wprowadzić <xref:System.Diagnostics.EventLog> jako import użytkownika i zastąpić <xref:System.Diagnostics.Debug> za pomocą funkcji aktualizacji.

### <a name="to-add-a-user-import"></a>Aby dodać import użytkownika

1. W **Eksploratorze rozwiązań**kliknij dwukrotnie węzeł **Mój projekt** dla projektu.

2. W **Projektancie projektów**kliknij kartę **Odwołania.**

3. W polu tekstowym poniżej listy **Importowane przestrzenie nazw** wprowadź pełną nazwę obszaru nazw, który chcesz zaimportować, w tym główny obszar nazw.

4. Kliknij przycisk **Dodaj importuj użytkownika,** aby dodać obszar nazw do listy **Importowane przestrzenie nazw.**

    > [!NOTE]
    > Przycisk **Dodaj importu użytkownika** zostanie wyłączony, jeśli obszar nazw pasuje do obszaru już na liście; nie można dodać importu dwa razy.

### <a name="to-update-a-user-import"></a>Aby zaktualizować import użytkownika

1. W **Eksploratorze rozwiązań**kliknij dwukrotnie węzeł **Mój projekt** dla projektu.

2. W **Projektancie projektów**kliknij kartę **Odwołania.**

3. Na liście **Importowane przestrzenie nazw** wybierz obszar nazw, który chcesz zmienić.

4. W polu tekstowym poniżej listy **Importowane przestrzenie nazw** wprowadź nazwę nowego obszaru nazw.

5. Kliknij przycisk **Aktualizuj import użytkownika,** aby zaktualizować obszar nazw na liście **Importowane przestrzenie nazw.**

## <a name="see-also"></a>Zobacz też

- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
