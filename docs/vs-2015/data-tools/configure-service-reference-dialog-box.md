---
title: Okno dialogowe Konfigurowanie odwołania do usługi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac8f4cf619bbdd007bb7aa570f549ae3c0b50e86
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651115"
---
# <a name="configure-service-reference-dialog-box"></a>Konfigurowanie odwołania do usługi — Okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno dialogowe **Konfigurowanie odwołania do usługi** umożliwia skonfigurowanie zachowania [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] usług.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Aby uzyskać dostęp do okna dialogowego **Konfigurowanie odwołania do usługi** , kliknij prawym przyciskiem myszy odwołanie do usługi w **Eksplorator rozwiązań** i wybierz polecenie **Konfiguruj odwołanie do usługi**. Możesz również uzyskać dostęp do okna dialogowego, klikając przycisk **Zaawansowane** w oknie **dialogowym Dodaj odwołanie do usługi**.

## <a name="task-list"></a>Lista zadań

- Aby zmienić adres, w którym jest hostowana usługa WCF, wprowadź nowy adres w polu **adres** .

- Aby zmienić poziom dostępu dla klas w kliencie WCF, wybierz słowo kluczowe poziomu dostępu na liście **poziom dostępu dla wygenerowanych klas** .

- Aby asynchronicznie wywoływać metody usługi WCF, zaznacz pole wyboru **Generuj operacje asynchroniczne** .

- Aby wygenerować typy kontraktów komunikatów w kliencie WCF, zaznacz pole wyboru **zawsze Generuj kontrakty komunikatów** .

- Aby określić typy kolekcji list lub słowników dla klienta WCF, wybierz typy z listy **Typ kolekcji** i **Typ kolekcji słownika** .

- Aby wyłączyć udostępnianie typów, wyczyść pole wyboru **Użyj ponownie typów w przywoływanych zestawach** . Aby włączyć udostępnianie typu dla podzbioru zestawów, do których się odwołuje, zaznacz pole wyboru **Użyj ponownie typów w przywoływanych zestawach** , wybierz pozycję **Użyj ponownie typów w określonych przywoływanych zestawach**i wybierz odpowiednie odwołania w **odwołaniach Lista zestawów**.

## <a name="uielement-list"></a>Lista elementów UI
 **Adres** Służy do aktualizowania adresu sieci Web, w którym odwołanie do usługi poszukuje usługi. Na przykład podczas programowania usługa może być hostowana na serwerze deweloperskim później przeniesiona na serwer produkcyjny, co wymaga zmiany adresu.

> [!NOTE]
> Element Address jest niedostępny, gdy okno dialogowe **Konfigurowanie odwołania do usługi** jest wyświetlane w oknie **dialogowym Dodaj odwołanie do usługi**.

 **Poziom dostępu do wygenerowanych klas** Określa poziom dostępu kodu dla klas klienta WCF.

> [!NOTE]
> W przypadku projektów witryny sieci Web Ta opcja jest zawsze ustawiana na `Public` i nie można jej zmienić. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z usługą](../data-tools/troubleshooting-service-references.md).

 **Generuj operacje asynchroniczne** Określa, czy metody usługi WCF będą wywoływane synchronicznie (wartość domyślna) czy asynchronicznie.

 **Generuj operacje oparte na zadaniach** Podczas pisania kodu asynchronicznego ta opcja umożliwia korzystanie z biblioteki zadań równoległych (TPL), która została wprowadzona w środowisku .NET 4. Zobacz [Biblioteka zadań równoległych (TPL)](https://msdn.microsoft.com/library/dd460717.aspx).

 **Zawsze Generuj kontrakty komunikatów** Określa, czy typy kontraktów komunikatów będą generowane dla klienta WCF. Aby uzyskać więcej informacji na temat umów dotyczących komunikatów, zobacz [Używanie kontraktów komunikatów](https://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).

 **Typ kolekcji** Określa typ kolekcji listy dla klienta WCF. Domyślny typ to <xref:System.Array>.

 **Typ kolekcji słownika** Określa typ kolekcji słownika dla klienta WCF. Domyślny typ to <xref:System.Collections.Generic.Dictionary%602>.

 **Ponowne używanie typów w przywoływanych zestawach** Określa, czy klient programu WCF podejmie próbę ponownego użycia, który już istnieje w przywoływanych zestawach zamiast generować nowe typy w przypadku dodania lub zaktualizowania usługi. Domyślnie ta opcja jest zaznaczona.

 **Użyj ponownie typów we wszystkich przywoływanych zestawach** Po wybraniu wszystkie typy na **liście przywoływanych zestawów** będą ponownie używane, jeśli jest to możliwe. Domyślnie ta opcja jest zaznaczona.

 **Użyj ponownie typów w określonych przywoływanych zestawach** Po wybraniu zostaną ponownie użyte tylko wybrane typy z **listy przywoływanych zestawów** .

 **Lista zestawów, do których się odwołuje** Zawiera listę przywoływanych zestawów dla projektu lub witryny sieci Web. Gdy wybrano **ponowne użycie typów w określonych przywoływanych zestawach** , poszczególne zestawy mogą być wybierane lub wyczyszczone.

 **Dodaj odwołanie sieci Web** Wyświetla okno [dialogowe NIB: Dodaj odwołanie sieci Web](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).

> [!NOTE]
> Tej opcji należy używać tylko w przypadku projektów przeznaczonych dla [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] w wersji 2,0.

> [!NOTE]
> Przycisk **Dodaj odwołanie sieci Web** jest dostępny tylko wtedy, gdy w oknie **dialogowym Dodaj odwołanie do usługi**zostanie wyświetlone okno dialogowe **Konfigurowanie odwołania do usługi** .

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołania do usługi](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9) [: Dodawanie odwołania do usługi sieci Web](https://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168) [Windows Communication Foundation usług i usługi danych programu WCF](../data-tools/configure-service-reference-dialog-box.md)
