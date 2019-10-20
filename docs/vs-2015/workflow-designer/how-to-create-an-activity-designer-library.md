---
title: 'Instrukcje: Tworzenie biblioteki projektanta działań | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 63404d3d81c44ac4b8308d949cdb87df419f2e04
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662870"
---
# <a name="how-to-create-an-activity-designer-library"></a>Instrukcje: Tworzenie biblioteki projektanta działań
Niestandardowe projektanty działań umożliwiają tworzenie interfejsu użytkownika dla działania standardowego lub niestandardowego. Możesz kontrolować złożoność interfejsu użytkownika i mieć możliwość tworzenia więcej niż jednego projektanta działań dla działania. Ten scenariusz umożliwia tworzenie projektantów, które są dostosowane do wielu odbiorców.

### <a name="to-create-an-activity-designer-library"></a>Aby utworzyć bibliotekę projektanta działań

1. Rozpocznij [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. W menu **plik** , wskaż **Nowy**, a następnie wybierz **projekt...** Aby otworzyć okno dialogowe **Nowy projekt** .

3. W okienku **typy projektów** wybierz pozycję **przepływ pracy** z poziomu grupowania **wizualizacji C#**  lub **Visual Basic** w zależności od preferowanego języka.

4. W okienku **Szablony** wybierz pozycję **Biblioteka projektanta działań**.

5. W polu **Nazwa** Wprowadź opisową nazwę projektu, aby ułatwić jego identyfikację.

6. W polu **Lokalizacja** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** , aby przejść do niego.

7. W polu **rozwiązanie** wpisz nazwę opisową rozwiązania, a następnie kliknij przycisk **OK**.

    > [!NOTE]
    > Jeśli chcesz dodać aplikację konsoli przepływu pracy do istniejącego rozwiązania, Otwórz to rozwiązanie w [!INCLUDE[vs2010](../includes/vs2010-md.md)], kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Dodaj**, a następnie **Nowy projekt...** Aby otworzyć okno dialogowe **Nowy projekt** . Postępuj zgodnie z powyższym opisem w tej procedurze.

8. Szablon projektu tworzy definicję projektanta działań w języku XAML i plik implementacji związany z kodem w kodzie źródłowym. Zostanie otwarty [!INCLUDE[wfd1](../includes/wfd1-md.md)] i zostanie wyświetlona Kanwa projektanta działań.

9. Przeciągnij kontrolki [!INCLUDE[avalon1](../includes/avalon1-md.md)] z **przybornika** na powierzchnię projektu, aby użyć ich w niestandardowym projektancie działań.  Aby zapoznać się z przykładem sposobu implementacji niestandardowego projektanta działań, zobacz [How to: Create an Custom Activity Designer](https://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31).

    > [!WARNING]
    > Niestandardowe Projektanci działań mogą służyć do działań niestandardowych, a także dla domyślnych [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]activities.

## <a name="see-also"></a>Zobacz też
 [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)