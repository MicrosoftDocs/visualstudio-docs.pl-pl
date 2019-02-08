---
title: 'Projektant przepływu pracy — jak: Dodawanie działań do przybornika'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e334ee23a68a4fbbb481765997ea1668daede13f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55940688"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Instrukcje: Dodawanie działań do przybornika

Działania mogą być dodawane do **przybornika** w rozwiązaniu na kilka różnych sposobów. Możesz dodać je z w obrębie bieżącego projektu, odwoływać się do nich z innego projektu lub odwoływać się do nich z innego zestawu.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Aby dodać działanie z w obrębie bieżącego projektu

1.  Dodaj nowe niestandardowe działanie bieżącego projektu przepływu pracy. Aby uzyskać więcej informacji na temat dodawania nowego niestandardowego działania do projektu, zobacz [jak: Dodaj nowy element do projektu przepływu pracy](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2.  Dodawanie logiki niestandardowej do działania.

3.  Skompiluj projekt. Jeśli kompilacja zakończyła się pomyślnie, Nowa kategoria **przybornika** o nazwie "\<*Nazwa projektu*>" jest wyświetlana przy użyciu niestandardowego działania zawarte w tej kategorii.

    > [!NOTE]
    > W przypadku zresetowania przybornika działań niestandardowych zostaną usunięte, nawet wtedy, gdy rozwiązanie jest stworzone ponownie. Ponownie wypełnić przybornika działań niestandardowych po został zresetowany, uruchom ponownie program Visual Studio.

    > [!NOTE]
    > Przybornik można wyświetlić tylko jednego działania imię. Jeśli dwa działania z różnych zestawów mają taką samą nazwę klasy, zostanie wyświetlona tylko jedna.

    > [!NOTE]
    > Domeny aplikacji jest współużytkowana przez Edytor wystąpień; Jeśli używane są statyczne zmienne, ich będzie współdzielona przez także wystąpienia edytora. Jeśli nie jest to zachowanie usługi powinny służyć do śledzenia zmiennej wystąpień. Zobacz [przy użyciu tego kontekstu do edycji elementu modelu](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) informacji na temat korzystania z usług w projektancie.

## <a name="to-add-an-activity-from-within-a-different-project"></a>Aby dodać działania z innego projektu

1.  Otwórz rozwiązanie, które zawiera co najmniej jeden projekt przepływu pracy i działania niestandardowego projektu biblioteki lub innego projektu przepływu pracy, który definiuje niestandardowe działanie.

2.  Twórz oba projekty. Jeśli kompilacje zakończyły się pomyślnie Nowa kategoria **przybornika** o nazwie "\<*Nazwa projektu*>" jest wyświetlana przy użyciu niestandardowego działania zawarte w tej kategorii.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Aby dodać działanie do przybornika z zestawu

1.  Otwórz rozwiązanie, przepływ pracy.

2.  Z **narzędzia** menu, wybierz opcję **wybierz elementy przybornika**.

3.  W **wybierz elementy przybornika** okno dialogowe, wybierz opcję **karty składniki elementu System.Activities** kartę, a następnie kliknij przycisk **Przeglądaj** można przejść do zestawu, który zawiera niestandardowy działanie, które chcesz dodać.

4.  Wybierz zestaw, a następnie kliknij przycisk **OK**. Składnik niestandardowe działanie zostanie dodany do listy składników i to opcja wybrana automatycznie.

    1.  Kliknij przycisk **OK** aby zamknąć okno dialogowe.

5.  Aby wyświetlić przybornik, wybierz pozycję **przybornika** z **widoku** menu.

6.  Niestandardowe działanie jest wyświetlana w **przybornika** kategorii, która była w trybie koncentracji uwagi, zanim element został dodany. Na przykład jeśli **ogólne** kategorii zostało wybrane w **przybornika** przed dodaniem elementu przybornika, działanie pojawiło się w obszarze **ogólne** kategorii.

## <a name="see-also"></a>Zobacz także

- [Używanie projektanta przepływu pracy](developing-applications-with-the-workflow-designer.md)