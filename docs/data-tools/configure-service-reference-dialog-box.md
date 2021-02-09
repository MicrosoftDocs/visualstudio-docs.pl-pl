---
title: Konfigurowanie odwołania do usługi — Okno dialogowe
description: Okno dialogowe Konfigurowanie odwołania do usługi w programie Visual Studio służy do konfigurowania zachowania usług Windows Communication Foundation (WCF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 9ce4057378db357345869d10e933929ae31ee573
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859219"
---
# <a name="configure-service-reference-dialog-box"></a>Konfiguruj odwołanie do usługi — Okno dialogowe

Okno dialogowe **Konfigurowanie odwołania do usługi** umożliwia skonfigurowanie zachowania usług Windows Communication Foundation (WCF).

Aby uzyskać dostęp do okna dialogowego **Konfigurowanie odwołania do usługi** , kliknij prawym przyciskiem myszy odwołanie do usługi w **Eksplorator rozwiązań** i wybierz polecenie **Konfiguruj odwołanie do usługi**. Możesz również uzyskać dostęp do okna dialogowego, klikając przycisk **Zaawansowane** w oknie **dialogowym Dodaj odwołanie do usługi**.

## <a name="task-list"></a>Lista zadań

- Aby zmienić adres, w którym jest hostowana usługa WCF, wprowadź nowy adres w polu **adres** .

- Aby zmienić poziom dostępu dla klas w kliencie WCF, wybierz słowo kluczowe poziomu dostępu na liście **poziom dostępu dla wygenerowanych klas** .

- Aby asynchronicznie wywoływać metody usługi WCF, zaznacz pole wyboru **Generuj operacje asynchroniczne** .

- Aby wygenerować typy kontraktów komunikatów w kliencie WCF, zaznacz pole wyboru **zawsze Generuj kontrakty komunikatów** .

- Aby określić typy kolekcji list lub słowników dla klienta WCF, wybierz typy z listy **Typ kolekcji** i **Typ kolekcji słownika** .

- Aby wyłączyć udostępnianie typów, wyczyść pole wyboru **Użyj ponownie typów w przywoływanych zestawach** . Aby włączyć udostępnianie typu dla podzbioru przywoływanych zestawów, zaznacz pole wyboru **Użyj ponownie typów w przywoływanych zestawach** , wybierz pozycję **Użyj ponownie typów w określonych przywoływanych zestawach** i wybierz odpowiednie odwołania na **liście przywoływanych zestawów**.

## <a name="uielement-list"></a>Lista elementów UIElement

**Adres**

Aktualizuje adres sieci Web, w którym odwołanie do usługi poszukuje usługi. Na przykład podczas opracowywania usługa może być hostowana na serwerze deweloperskim, a następnie przeniesiona na serwer produkcyjny, co wymaga zmiany adresu.

> [!NOTE]
> Element Address jest niedostępny, gdy okno dialogowe **Konfigurowanie odwołania do usługi** jest wyświetlane w oknie **dialogowym Dodaj odwołanie do usługi**.

**Poziom dostępu do wygenerowanych klas**

Określa poziom dostępu kodu dla klas klienta WCF.

> [!NOTE]
> W przypadku projektów witryny sieci Web Ta opcja jest zawsze ustawiana na `Public` i nie można jej zmienić. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z usługą](../data-tools/troubleshooting-service-references.md).

**Generuj operacje asynchroniczne**

Określa, czy metody usługi WCF są wywoływane synchronicznie (wartość domyślna) czy asynchronicznie.

**Generuj operacje oparte na zadaniach**

Podczas pisania kodu asynchronicznego ta opcja umożliwia korzystanie z biblioteki zadań równoległych (TPL), która została wprowadzona w programie .NET 4. Zobacz [Biblioteka zadań równoległych (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

**Zawsze Generuj kontrakty komunikatów**

Określa, czy typy kontraktów komunikatów są generowane dla klienta WCF. Aby uzyskać więcej informacji na temat umów dotyczących komunikatów, zobacz [Używanie kontraktów komunikatów](/dotnet/framework/wcf/feature-details/using-message-contracts).

**Typ kolekcji**

Określa typ kolekcji listy dla klienta WCF. Domyślnym typem jest <xref:System.Array> .

**Typ kolekcji słownika**

Określa typ kolekcji słownika dla klienta WCF. Domyślnym typem jest <xref:System.Collections.Generic.Dictionary%602> .

**Ponowne używanie typów w przywoływanych zestawach**

Określa, czy klient WCF próbuje ponownie użyć tego, co już istnieje w przywoływanych zestawach, zamiast generować nowe typy w przypadku dodania lub zaktualizowania usługi. Domyślnie ta opcja jest zaznaczona.

**Użyj ponownie typów we wszystkich przywoływanych zestawach**

W przypadku wybrania tej listy wszystkie typy na **liście przywoływanych zestawów** są ponownie używane, jeśli jest to możliwe. Ta opcja jest wybrana domyślnie.

**Użyj ponownie typów w określonych przywoływanych zestawach**

Po wybraniu są ponownie używane tylko wybrane typy z **listy przywoływanych zestawów** .

**Lista zestawów, do których się odwołuje**

Zawiera listę zestawów, do których odwołuje się projekt lub witryna sieci Web. W przypadku wybrania opcji **Użyj ponownie typów w określonych przywoływanych zestawach** można wybrać lub wyczyścić poszczególne zestawy.

**Dodaj odwołanie sieci Web**

Wyświetla okno dialogowe **Dodawanie odwołania sieci Web** .

> [!NOTE]
> Tej opcji należy używać tylko w przypadku projektów przeznaczonych dla .NET Framework w wersji 2,0.
>
> [!NOTE]
> Przycisk **Dodaj odwołanie sieci Web** jest dostępny tylko wtedy, gdy w oknie **dialogowym Dodaj odwołanie do usługi** zostanie wyświetlone okno dialogowe **Konfigurowanie odwołania do usługi** .

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Dodawanie odwołania do usługi sieci Web](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Usługi Windows Communication Foundation i usługi danych programu WCF](../data-tools/configure-service-reference-dialog-box.md)
