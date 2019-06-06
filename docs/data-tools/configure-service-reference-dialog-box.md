---
title: Konfigurowanie odwołania do usługi — Okno dialogowe
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7ca5f71d386f48b36fcb1126a1e0467b40ef8d73
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745582"
---
# <a name="configure-service-reference-dialog-box"></a>Konfiguruj odwołanie do usługi — Okno dialogowe

**Konfiguruj odwołanie do usługi** okno dialogowe umożliwia konfigurowanie zachowania usług Windows Communication Foundation (WCF).

Aby uzyskać dostęp do **Konfiguruj odwołanie do usługi** odwoływać się okno dialogowe, kliknij prawym przyciskiem myszy, a usługa **Eksploratora rozwiązań** i wybierz polecenie **Konfiguruj odwołanie do usługi**. Okno dialogowe można również przejść, klikając **zaawansowane** znajdujący się w **okno dialogowe Dodaj odwołanie do usługi**.

## <a name="task-list"></a>Lista zadań

- Aby zmienić adres, na którym jest hostowana usługa WCF, wprowadź nowy adres w **adres** pola.

- Aby zmienić poziom dostępu dla klas w klienta WCF, wybierz słowo kluczowe poziom dostępu w **poziom do wygenerowanych klas dostępu** listy.

- Aby asynchroniczne wywoływanie metod klasy usługi WCF, wybierz pozycję **Eneruj operacje asynchroniczne** pole wyboru.

- Aby wygenerować typy kontraktu komunikatu w klienta WCF, wybierz **zawsze Generuj kontrakty komunikatów** pole wyboru.

- Aby określić typy kolekcji list lub słownika dla klienta programu WCF, wybierz typy z **— typ kolekcji** i **słownikowy typ kolekcji** listy.

- Aby wyłączyć, typ udostępniania, wyczyść **ponownie użyj typów w przywoływanych zestawach** pole wyboru. Aby włączyć udostępnianie dla podzbioru przywoływanych zestawach typu, wybierz **ponownie użyj typów w przywoływanych zestawach** pole wyboru, wybierz opcję **ponownie użyj typów w określonych przywoływanych zestawach**i wybierz żądany przywoływane w **przywoływane zestawy listy**.

## <a name="uielement-list"></a>Lista elementów interfejsu użytkownika

 **Adres**

 Aktualizuje adres sieci web, w której odwołanie do usługi szuka usługi. Na przykład podczas tworzenia aplikacji, usługa może być hostowana na serwerze rozwoju i później przenieść na serwerze produkcyjnym, przez co konieczna zmiana adresu.

> [!NOTE]
> Element adres nie jest dostępna podczas **Konfiguruj odwołanie do usługi** zostanie wyświetlone okno dialogowe z **okno dialogowe Dodaj odwołanie do usługi**.

 **Poziom dostępu do wygenerowanych klas**

 Określa poziom dostępu do kodu dotyczące klas klientów usługi WCF.

> [!NOTE]
> Dla projektów witryny sieci Web, ta opcja jest zawsze równa `Public` i nie można zmienić. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z odwołaniami usługi](../data-tools/troubleshooting-service-references.md).

 **Generowanie operacji asynchronicznych**

 Określa, czy metody usługi WCF jest wywoływana synchronicznie (ustawienie domyślne) lub asynchronicznie.

 **Generuj operacje oparte na zadanie**

 Podczas pisania kodu asynchronicznego, ta opcja pozwala korzystać z Biblioteka zadań równoległych (TPL) wprowadzone za pomocą .NET 4. Zobacz [zadań Biblioteka równoległych (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

 **Zawsze Generuj kontrakty komunikatów**

 Określa, czy typy kontraktu komunikatu, są generowane dla klienta programu WCF. Aby uzyskać więcej informacji na temat kontraktów komunikatu zobacz [używanie kontraktów komunikatu](/dotnet/framework/wcf/feature-details/using-message-contracts).

 **Typ kolekcji**

 Określa typ kolekcji listy dla klienta programu WCF. Domyślny typ to <xref:System.Array>.

 **Słownikowy typ kolekcji**

 Określa słownikowy typ kolekcji dla klienta programu WCF. Domyślny typ to <xref:System.Collections.Generic.Dictionary%602>.

 **Użyj ponownie typów w przywoływanych zestawach**

 Określa, czy klient WCF podejmie próbę ponownego użycia, co już istnieje w przywoływanych zestawach zamiast generowania nowych typów, gdy usługa jest dodane lub zaktualizowane. Domyślnie ta opcja jest zaznaczona.

 **Użyj ponownie typów w wszystkich przywoływanych zestawach**

 Po wybraniu wszystkich typów w **listę zestawów do którego się odwoływano** są ponownie, jeśli jest to możliwe. Domyślnie ta opcja jest zaznaczona.

 **Ponownie użyj typów w określonych przywoływanych zestawach**

 W przypadku wybrania tylko wybranych typów w **listę zestawów do którego się odwoływano** są ponownie używane.

 **Listę przywoływanych zestawach**

 Zawiera listę przywoływanych zestawach dla projektu lub witryny sieci Web. Po wybraniu **ponownie użyj typów w określonych przywoływanych zestawach**, można zaznaczyć lub wyczyścić poszczególnych zespołów.

 **Dodaj odwołanie sieci Web**

 Wyświetla **Dodaj odwołanie sieci Web** okno dialogowe.

> [!NOTE]
> Ta opcja powinna używana tylko dla projektów przeznaczonych dla wersji 2.0 programu .NET Framework.
>
> [!NOTE]
> **Dodaj odwołanie sieci Web** przycisk jest dostępny, gdy **Konfiguruj odwołanie do usługi** zostanie wyświetlone okno dialogowe z **okno dialogowe Dodaj odwołanie do usługi**.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dodaj odwołanie do usługi sieci web](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Usługi Windows Communication Foundation i usługi danych programu WCF](../data-tools/configure-service-reference-dialog-box.md)