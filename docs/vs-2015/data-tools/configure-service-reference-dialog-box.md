---
title: Konfigurowanie usługi odwołania — okno dialogowe | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 18ea294c204f1512aaa3eeae904eed52edf8e9f2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114148"
---
# <a name="configure-service-reference-dialog-box"></a>Konfigurowanie odwołania do usługi — Okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Konfiguruj odwołanie do usługi** okno dialogowe umożliwia konfigurowanie zachowania [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] usług.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Aby uzyskać dostęp do **Konfiguruj odwołanie do usługi** odwoływać się okno dialogowe, kliknij prawym przyciskiem myszy, a usługa **Eksploratora rozwiązań** i wybierz polecenie **Konfiguruj odwołanie do usługi**. Okno dialogowe można również przejść, klikając **zaawansowane** znajdujący się w **okno dialogowe Dodaj odwołanie do usługi**.  
  
## <a name="task-list"></a>Lista zadań  
  
- Aby zmienić adres, na którym jest hostowana usługa WCF, wprowadź nowy adres w **adres** pola.  
  
- Aby zmienić poziom dostępu dla klas w klienta WCF, wybierz słowo kluczowe poziom dostępu w **poziom do wygenerowanych klas dostępu** listy.  
  
- Aby asynchroniczne wywoływanie metod klasy usługi WCF, wybierz pozycję **Eneruj operacje asynchroniczne** pole wyboru.  
  
- Aby wygenerować typy kontraktu komunikatu w klienta WCF, wybierz **zawsze Generuj kontrakty komunikatów** pole wyboru.  
  
- Aby określić typy kolekcji list lub słownika dla klienta programu WCF, wybierz typy z **— typ kolekcji** i **słownikowy typ kolekcji** listy.  
  
- Aby wyłączyć, typ udostępniania, wyczyść **ponownie użyj typów w przywoływanych zestawach** pole wyboru. Aby włączyć udostępnianie dla podzbioru przywoływanych zestawach typu, wybierz **ponownie użyj typów w przywoływanych zestawach** pole wyboru, wybierz opcję **ponownie użyj typów w określonych przywoływanych zestawach**i wybierz żądany przywoływane w **przywoływane zestawy listy**.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Adres**  
 Używane do aktualizowania adres sieci Web, w których odwołanie do usługi szuka usługi. Na przykład podczas tworzenia usługi może być hostowana na serwerze rozwoju następnie później przenieść się na serwerze produkcyjnym, przez co konieczna zmiana adresu.  
  
> [!NOTE]
>  Element adres nie jest dostępna podczas **Konfiguruj odwołanie do usługi** zostanie wyświetlone okno dialogowe z **okno dialogowe Dodaj odwołanie do usługi**.  
  
 **Poziom dostępu do wygenerowanych klas**  
 Określa poziom dostępu do kodu dotyczące klas klientów usługi WCF.  
  
> [!NOTE]
>  Dla projektów witryny sieci Web, ta opcja jest zawsze równa `Public` i nie można zmienić. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z odwołaniami usługi](../data-tools/troubleshooting-service-references.md).  
  
 **Generowanie operacji asynchronicznych**  
 Określa, czy metody usługi WCF zostanie wywołana synchronicznie (ustawienie domyślne) lub asynchronicznie.  
  
 **Generuj operacje oparte na zadanie**  
 Podczas pisania kodu asynchronicznego, ta opcja umożliwia korzystanie z Biblioteka zadań równoległych (TPL) wprowadzone przy użyciu platformy .net 4. Zobacz [zadań Biblioteka równoległych (TPL)](http://msdn.microsoft.com/library/dd460717.aspx).  
  
 **Zawsze Generuj kontrakty komunikatów**  
 Określa, czy typy kontraktu komunikatu, zostanie wygenerowany dla klienta programu WCF. Aby uzyskać więcej informacji na temat kontraktów komunikatu zobacz [za pomocą kontraktów komunikatu](http://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).  
  
 **Typ kolekcji**  
 Określa typ kolekcji listy dla klienta programu WCF. Domyślny typ to <xref:System.Array>.  
  
 **Słownikowy typ kolekcji**  
 Określa słownikowy typ kolekcji dla klienta programu WCF. Domyślny typ to <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Użyj ponownie typów w przywoływanych zestawach**  
 Określa, czy klient WCF podejmie próbę ponownego użycia już istniejące w przywoływanych zestawach zamiast generowania nowych typów, gdy usługa jest dodane lub zaktualizowane. Domyślnie ta opcja jest zaznaczona.  
  
 **Użyj ponownie typów w wszystkich przywoływanych zestawach**  
 Po wybraniu wszystkich typów w **listę zestawów do którego się odwoływano** zostanie ponownie użyty, jeśli jest to możliwe. Domyślnie ta opcja jest zaznaczona.  
  
 **Ponownie użyj typów w określonych przywoływanych zestawach**  
 W przypadku wybrania tylko wybranych typów w **listę zestawów do którego się odwoływano** zostanie ono użyte ponownie.  
  
 **Listę przywoływanych zestawach**  
 Zawiera listę przywoływanych zestawach dla projektu lub witryny sieci Web. Gdy **ponownie użyj typów w określonych przywoływanych zestawach** jest zaznaczone, pojedyncze zestawy można zaznaczyć lub wyczyścić.  
  
 **Dodaj odwołanie sieci Web**  
 Wyświetla [NIB: Dodaj odwołanie sieci Web, okno dialogowe](http://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).  
  
> [!NOTE]
>  Ta opcja powinna być używana tylko dla projektów przeznaczonych dla wersji 2.0 programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  **Dodaj odwołanie sieci Web** przycisk jest dostępny tylko wtedy, gdy **Konfiguruj odwołanie do usługi** zostanie wyświetlone okno dialogowe z **okno dialogowe Dodaj odwołanie do usługi**.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołań usługi](http://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)   
 [Instrukcje: Dodaj odwołanie do usługi sieci Web](http://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168)   
 [Usługi Windows Communication Foundation i usługi danych programu WCF](../data-tools/configure-service-reference-dialog-box.md)
