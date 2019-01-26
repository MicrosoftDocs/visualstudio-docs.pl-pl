---
title: 'Instrukcje: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic)'
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 806fcb9ee4dd078301095192df8cb143cc085161
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021510"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Instrukcje: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic)

Importowanie przestrzeni nazw pozwala na używanie elementów z tej przestrzeni nazw w kodzie bez w pełni kwalifikowanie elementu. Na przykład, jeśli chcesz uzyskać dostęp do `Create` method in Class metoda `System.Messaging.MessageQueue` klasy, można zaimportować `System.Messaging` przestrzeni nazw i po prostu odwoływać się do elementu, należy w kodzie jako `MessageQueue.Create`.

 Importowane przestrzenie nazw są zarządzane na **odwołania** strony **projektanta projektu**. Polecenie importuje określisz w tym oknie dialogowym są przekazywane bezpośrednio do kompilatora (*/importuje*) i Zastosuj do wszystkich plików w projekcie. Użyj `Imports` instrukcję, aby użyć przestrzeni nazw w pliku kodu jednego źródła.

### <a name="to-add-an-imported-namespace"></a>Aby dodać importowanych przestrzeni nazw

1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **mój projekt** węzeł dla projektu.

2.  W **projektanta projektu**, kliknij przycisk **odwołania** kartę.

3.  W **zaimportowane przestrzenie nazw** listy, zaznacz pole wyboru dla przestrzeni nazw, który chcesz dodać.

    > [!NOTE]
    >  W celu zaimportowania, przestrzeń nazw musi być w składnika. Przestrzeń nazw nie ma na liście, należy dodać odwołanie do składnika, który go zawiera. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](managing-references-in-a-project.md).

### <a name="to-remove-an-imported-namespace"></a>Aby usunąć importowanych przestrzeni nazw

1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **mój projekt** węzeł dla projektu.

2.  W **projektanta projektu**, kliknij przycisk **odwołania** kartę.

3.  W **zaimportowane przestrzenie nazw** listy, usuń zaznaczenie pola wyboru dla przestrzeni nazw, który chcesz usunąć.

## <a name="user-imports"></a>Importy użytkownika
 Importy użytkownika umożliwiają importowanie określonej klasy w przestrzeni nazw, a nie cały obszar nazw. Na przykład aplikacja może mieć import dla <xref:System.Diagnostics> przestrzeni nazw, ale to jedyna klasa w obrębie tej przestrzeni nazw, który Cię interesuje `Debug` klasy. Można zdefiniować <xref:System.Diagnostics.Debug> jako użytkownik zaimportować, a następnie usuń import dla <xref:System.Diagnostics>.

 Jeśli później zmienić należy pamiętać i zdecyduj, który był naprawdę `EventLog` klasy potrzebne, można wprowadzić <xref:System.Diagnostics.EventLog> jako użytkownik zaimportować, a następnie zastąpić <xref:System.Diagnostics.Debug> przy użyciu funkcji aktualizacji.

### <a name="to-add-a-user-import"></a>Można dodać importu użytkowników

1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **mój projekt** węzeł dla projektu.

2.  W **projektanta projektu**, kliknij przycisk **odwołania** kartę.

3.  W poniższym polu tekstowym **zaimportowane przestrzenie nazw** listy, należy wprowadzić pełną nazwę przestrzeni nazw, które chcesz zaimportować, włącznie z przestrzenią nazw głównych.

4.  Kliknij przycisk **dodać import użytkownika** przycisk, aby dodać przestrzeń nazw w celu **zaimportowane przestrzenie nazw** listy.

    > [!NOTE]
    > **Dodać import użytkownika** przycisk będzie wyłączony, jeśli przestrzeń nazw pasuje do już na liście; nie można dodać importu, dwa razy.

### <a name="to-update-a-user-import"></a>Aby zaktualizować importu użytkowników

1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **mój projekt** węzeł dla projektu.

2.  W **projektanta projektu**, kliknij przycisk **odwołania** kartę.

3.  W **zaimportowane przestrzenie nazw** listy, wybierz przestrzeń nazw, którą chcesz zmienić.

4.  W poniższym polu tekstowym **zaimportowane przestrzenie nazw** listy, wprowadź nazwę dla nowej przestrzeni nazw.

5.  Kliknij przycisk **aktualizacji importu użytkownika** przycisk, aby zaktualizować przestrzeni nazw w **zaimportowane przestrzenie nazw** listy.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)