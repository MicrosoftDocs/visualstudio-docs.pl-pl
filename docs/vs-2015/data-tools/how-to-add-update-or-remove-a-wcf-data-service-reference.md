---
title: 'Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołania do usługi danych programu WCF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89a667e3254be8161d4defb54d524756a5eb02fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670010"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Porady: dodawanie, aktualizowanie lub usuwanie odwołań usługi danych WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Odwołanie do usługi* umożliwia projektowi dostęp do co najmniej jednego elementu [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] . Użyj okna dialogowego **Dodaj odwołanie do usługi** , aby wyszukać [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] w bieżącym rozwiązaniu, lokalnie, w sieci lokalnej lub w Internecie.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-a-service-reference"></a>Dodawanie odwołania do usługi

#### <a name="to-add-a-reference-to-an-external-service"></a>Aby dodać odwołanie do usługi zewnętrznej

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać usługę, a następnie kliknij pozycję **Dodaj odwołanie do usługi**.

     Zostanie wyświetlone okno dialogowe **Dodaj odwołanie do usługi** .

2. W polu **adres** wprowadź adres URL usługi, a następnie kliknij przycisk **Przejdź** , aby wyszukać usługę. Jeśli usługa implementuje zabezpieczenia nazwy użytkownika i hasła, może zostać wyświetlony monit o podanie nazwy użytkownika i hasła.

    > [!NOTE]
    > Należy tylko odwoływać się do usług z zaufanego źródła. Dodanie odwołań z niezaufanego źródła może spowodować naruszenie zabezpieczeń.

     Możesz również wybrać adres URL z listy **adres** , który przechowuje poprzednie 15 adresów URL, na których znaleziono prawidłowe metadane usługi.

     Podczas wykonywania wyszukiwania jest wyświetlany pasek postępu. Wyszukiwanie można zatrzymać w dowolnym momencie, klikając przycisk **Zatrzymaj**.

3. Na liście **usługi** rozwiń węzeł usługi, która ma zostać użyta, a następnie wybierz zestaw jednostek.

4. W polu **przestrzeń nazw** wprowadź przestrzeń nazw, która ma być używana dla odwołania.

5. Kliknij przycisk **OK** , aby dodać odwołanie do projektu.

     Zostanie wygenerowany klient usługi (proxy), a metadane opisujące usługę zostaną dodane do pliku app.config.

#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Aby dodać odwołanie do usługi w bieżącym rozwiązaniu

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać usługę, a następnie kliknij pozycję **Dodaj odwołanie do usługi**.

     Zostanie wyświetlone okno dialogowe **Dodaj odwołanie do usługi** .

2. Kliknij pozycję **Odnajdź**.

     Wszystkie usługi ( [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] i usługi WCF) w bieżącym rozwiązaniu są dodawane do listy **usług** .

3. Na liście **usługi** rozwiń węzeł usługi, która ma zostać użyta, a następnie wybierz zestaw jednostek.

4. W polu **przestrzeń nazw** wprowadź przestrzeń nazw, która ma być używana dla odwołania.

5. Kliknij przycisk **OK** , aby dodać odwołanie do projektu.

     Zostanie wygenerowany klient usługi (proxy), a metadane opisujące usługę zostaną dodane do pliku app.config.

## <a name="updating-a-service-reference"></a>Aktualizowanie odwołania do usługi
 Entity Data Model dla a [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] czasami ulegnie zmianie. W takim przypadku należy zaktualizować odwołanie do usługi.

#### <a name="to-update-a-service-reference"></a>Aby zaktualizować odwołanie do usługi

- W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy odwołanie do usługi, a następnie kliknij pozycję **Aktualizuj odwołanie do usługi**.

     Zostanie wyświetlone okno dialogowe postęp, gdy odwołanie zostanie zaktualizowane z jego oryginalnej lokalizacji, a klient usługi zostanie wygenerowany ponownie w celu odzwierciedlenia zmian w metadanych.

## <a name="removing-a-service-reference"></a>Usuwanie odwołania do usługi
 Jeśli odwołanie do usługi nie jest już używane, można je usunąć z rozwiązania.

#### <a name="to-remove-a-service-reference"></a>Aby usunąć odwołanie do usługi

- W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy odwołanie do usługi, a następnie kliknij pozycję **Usuń**.

     Klient usługi zostanie usunięty z rozwiązania, a metadane opisujące usługę zostaną usunięte z pliku app.config.

    > [!NOTE]
    > Każdy kod odwołujący się do odwołania do usługi będzie musiał zostać usunięty ręcznie.

## <a name="see-also"></a>Zobacz też
 [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
