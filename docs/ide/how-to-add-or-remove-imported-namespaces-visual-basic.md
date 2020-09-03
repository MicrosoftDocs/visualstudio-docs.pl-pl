---
title: 'Instrukcje: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic)'
ms.date: 06/21/2017
ms.topic: how-to
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
ms.openlocfilehash: a50fdb643029bed8a44ce6999d4a8ce062ba3dcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284742"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Instrukcje: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic)

Importowanie przestrzeni nazw pozwala używać elementów z tej przestrzeni nazw w kodzie bez w pełni zakwalifikowania elementu. Na przykład jeśli chcesz uzyskać dostęp do `Create` metody w `System.Messaging.MessageQueue` klasie, możesz zaimportować `System.Messaging` przestrzeń nazw i odwołać się do elementu, który jest potrzebny w kodzie jako `MessageQueue.Create` .

Importowane przestrzenie nazw są zarządzane na stronie **odwołania** **projektanta projektu**. Importy określone w tym oknie dialogowym są przesyłane bezpośrednio do kompilatora (*/Imports —*) i stosowane do wszystkich plików w projekcie. Użyj `Imports` instrukcji, aby użyć przestrzeni nazw w jednym pliku kodu źródłowego.

### <a name="to-add-an-imported-namespace"></a>Aby dodać zaimportowaną przestrzeń nazw

1. W **Eksplorator rozwiązań**kliknij dwukrotnie węzeł **mój projekt** dla projektu.

2. W **projektancie projektu**kliknij kartę **odwołania** .

3. Na liście **zaimportowanych obszarów nazw** zaznacz pole wyboru dla przestrzeni nazw, którą chcesz dodać.

    > [!NOTE]
    > W celu zaimportowania przestrzeń nazw musi znajdować się w składniku, do którego się odwołuje. Jeśli przestrzeń nazw nie występuje na liście, należy dodać odwołanie do składnika, który go zawiera. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](managing-references-in-a-project.md).

### <a name="to-remove-an-imported-namespace"></a>Aby usunąć zaimportowaną przestrzeń nazw

1. W **Eksplorator rozwiązań**kliknij dwukrotnie węzeł **mój projekt** dla projektu.

2. W **projektancie projektu**kliknij kartę **odwołania** .

3. Na liście **zaimportowanych obszarów nazw** Usuń zaznaczenie pola wyboru dla przestrzeni nazw, która ma zostać usunięta.

## <a name="user-imports"></a>Importy użytkowników
Importy użytkowników umożliwiają importowanie określonej klasy w przestrzeni nazw, a nie całej przestrzeni nazw. Na przykład aplikacja może mieć import dla <xref:System.Diagnostics> przestrzeni nazw, ale jedyną klasą w tej przestrzeni nazw, która Cię interesuje, jest `Debug` Klasa. Można zdefiniować <xref:System.Diagnostics.Debug> jako import użytkownika, a następnie usunąć import dla <xref:System.Diagnostics> .

Jeśli później zmienisz zdanie i zdecydujesz, że naprawdę była to `EventLog` wymagana Klasa, możesz wprowadzić <xref:System.Diagnostics.EventLog> jako import i zastępować użytkownika <xref:System.Diagnostics.Debug> przy użyciu funkcji aktualizacji.

### <a name="to-add-a-user-import"></a>Aby dodać Importowanie użytkownika

1. W **Eksplorator rozwiązań**kliknij dwukrotnie węzeł **mój projekt** dla projektu.

2. W **projektancie projektu**kliknij kartę **odwołania** .

3. W polu tekstowym pod listą **importowanych obszarów nazw** wprowadź pełną nazwę przestrzeni nazw, która ma zostać zaimportowana, w tym główną przestrzeń nazw.

4. Kliknij przycisk **Dodaj Import użytkownika** , aby dodać przestrzeń nazw do listy **importowanych obszarów nazw** .

    > [!NOTE]
    > Przycisk **Dodaj Import użytkownika** zostanie wyłączony, jeśli przestrzeń nazw pasuje do jednego z nich znajdującego się już na liście; nie można dodać importu dwa razy.

### <a name="to-update-a-user-import"></a>Aby zaktualizować Importowanie użytkownika

1. W **Eksplorator rozwiązań**kliknij dwukrotnie węzeł **mój projekt** dla projektu.

2. W **projektancie projektu**kliknij kartę **odwołania** .

3. Z listy **zaimportowanych obszarów nazw** wybierz przestrzeń nazw, którą chcesz zmienić.

4. W polu tekstowym pod listą **importowanych obszarów** nazw wprowadź nazwę nowej przestrzeni nazw.

5. Kliknij przycisk **Aktualizuj Import użytkowników** , aby zaktualizować przestrzeń nazw na liście **zaimportowanych przestrzeni nazw** .

## <a name="see-also"></a>Zobacz też

- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
