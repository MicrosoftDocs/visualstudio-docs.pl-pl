---
title: 'Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołań usługi danych WCF'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 201f04852dea58d51cae10e98429f7b5f2bc6951
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945459"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołań usługi danych WCF
A *sług* umożliwia dostęp do co najmniej jeden projekt [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Użyj **Dodaj odwołanie do usługi** okno dialogowe, aby wyszukać [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] w bieżącym rozwiązaniu lokalnie, w sieci lokalnej lub w Internecie.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>Dodaj odwołanie do usługi

### <a name="to-add-a-reference-to-an-external-service"></a>Aby dodać odwołanie do usługi zewnętrznej

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać usługę, a następnie kliknij przycisk **Dodaj odwołanie do usługi**.

     **Dodaj odwołanie do usługi** pojawi się okno dialogowe.

2.  W **adres** , wprowadź adres URL dla usługi, a następnie kliknij **Przejdź** wyszukiwania dla usługi. Jeśli usługa implementuje zabezpieczenia nazwę i hasło użytkownika, może się monit o nazwę użytkownika i hasło.

    > [!NOTE]
    >  Użytkownik powinien odwoływać się tylko do usług z zaufanego źródła. Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.

     Możesz również wybrać adres URL z **adres** listy, w którym przechowywane są poprzednie 15 adresów URL, pod którymi — znaleziono metadane prawidłową usługę.

     Pasek postępu jest wyświetlana podczas wyszukiwania. Zatrzymać wyszukiwania w dowolnym momencie, klikając **zatrzymać**.

3.  W **usług** listy, rozwiń węzeł usługi, który chcesz użyć, a następnie wybierz zestaw jednostek.

4.  W **Namespace** wprowadź obszar nazw, który chcesz użyć dla odwołania.

5.  Kliknij przycisk **OK** można dodać odwołania do projektu.

     Klient usługi (proxy) jest generowany i metadane opisujące usługi jest dodawany do *app.config* pliku.

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Aby dodać odwołanie do usługi w bieżącym rozwiązaniu

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać usługę, a następnie kliknij przycisk **Dodaj odwołanie do usługi**.

    **Dodaj odwołanie do usługi** pojawi się okno dialogowe.

2. Kliknij przycisk **odnajdywanie**.

    Wszystkie usługi (zarówno [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] i usługi WCF) w bieżącym rozwiązaniu są dodawane do **usług** listy.

3. W **usług** listy, rozwiń węzeł usługi, który chcesz użyć, a następnie wybierz zestaw jednostek.

4. W **Namespace** wprowadź obszar nazw, który chcesz użyć dla odwołania.

5. Kliknij przycisk **OK** można dodać odwołania do projektu.

    Generuje klienta usługi (proxy), a metadane opisujące usługi jest dodawany do *app.config* pliku.

## <a name="update-a-service-reference"></a>Aktualizuj odwołanie do usługi
 Modelu Entity Data Model, aby uzyskać [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] czasami zmienia się. W takim przypadku należy zaktualizować odwołania do usługi.

### <a name="to-update-a-service-reference"></a>Aby zaktualizować odwołania do usługi

-   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy odwołanie do usługi, a następnie kliknij przycisk **odwołanie do usługi aktualizacji**.

     Okno dialogowe postępu Wyświetla, gdy odwołanie jest aktualizowany z oryginalnej lokalizacji, a klient usługi zostanie ponownie wygenerowany, aby odzwierciedlały zmiany w metadanych.

## <a name="remove-a-service-reference"></a>Usuwanie odwołań usługi
 Odwołanie do usługi jest już używany, możesz go usunąć z rozwiązania.

### <a name="to-remove-a-service-reference"></a>Aby usunąć odwołanie do usługi

-   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy odwołanie do usługi, a następnie kliknij przycisk **Usuń**.

     Klient usługi zostanie usunięty z rozwiązania oraz metadane opisujące usługi zostaną usunięte z *app.config* pliku.

    > [!NOTE]
    >  Każdy kod odwołujący się do odwołania do usługi muszą zostać usunięte ręcznie.

## <a name="see-also"></a>Zobacz także

- [Windows Communication Foundation i usługi WCF usług danych w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)