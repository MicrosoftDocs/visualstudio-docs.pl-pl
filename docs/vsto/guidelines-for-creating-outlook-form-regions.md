---
title: Wytyczne dotyczące tworzenia regionów formularzy programu Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a962b1ae2bff7b9a954204485a6ee73a3b63eb7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255950"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Wytyczne dotyczące tworzenia regionów formularzy programu Outlook
  Poniższe informacje mogą pomóc zoptymalizować regiony formularzy i uniknąć potencjalnych problemów:

- [Użyj nazw regionów formularza](#UsingFormRegions).

- [Wyłącz dziedziczenie regionu formularza](#DisablingInheritance).

- [Zrozumienie typów i nazw klas komunikatów](#ClassNames).

- [Projektuj sąsiednie regiony formularzy dla okienka odczytu](#ReadingPane).

- [Używaj optymalnych rozmiarów ikon](#UsingOptimal).

  Aby uzyskać więcej informacji na temat regionów formularzy, zobacz [Tworzenie regionów formularzy w programie Outlook](../vsto/creating-outlook-form-regions.md).

  [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="use-form-region-names"></a><a name="UsingFormRegions"></a> Użyj nazw regionów formularza
 Istnieje kilka nazw używanych do opisywania regionu formularza. Ważne jest, aby zrozumieć różnicę między tymi nazwami i wpływem na region formularza. Poniższa tabela opisuje każdą nazwę.

|Nazwa regionu formularza|Opis|
|----------------------|-----------------|
|Nazwa elementu regionu formularza|Nazwa określona dla elementu **region formularza programu Outlook** w oknie dialogowym **Dodaj nowy element** . Jest to nazwa pliku kodu regionu formularza, który pojawia się w **Eksplorator rozwiązań**.|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> wartość|Tę nazwę należy określić w **tekście opisowym i wybrać stronę Preferencje wyświetlania** w kreatorze **nowego regionu formularza programu Outlook** . Ta nazwa jest wyświetlana jako właściwość **FormRegionName** w oknie **Właściwości** .<br /><br /> Użyj <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> właściwości, aby określić etykietę identyfikującą region formularza w interfejsie użytkownika programu Outlook. W odniesieniu do odrębnych regionów formularza ta nazwa jest wyświetlana jako przycisk na Wstążce elementu programu Outlook.<br /><br /> W przypadku sąsiadujących regionów formularza ta nazwa jest wyświetlana jako tekst nagłówka powyżej regionu formularza.|
|Atrybut `Microsoft.Office.Tools.Outlook.FormRegionName`|Po dodaniu elementu **regionu formularza programu Outlook** do projektu program Visual Studio ustawia tę właściwość na w pełni kwalifikowaną nazwę regionu formularza. Domyślna w pełni kwalifikowana nazwa to nazwa dodatku VSTO połączonego z nazwą regionu formularza przez kropkę — na przykład `OutlookAddIn1.FormRegion1` .<br /><br /> Ta w pełni kwalifikowana nazwa jest również wyświetlana jako atrybut w górnej części klasy fabryki regionów formularza.<br /><br /> Użyj `Microsoft.Office.Tools.Outlook.FormRegionName` atrybutu, aby jednoznacznie identyfikować region formularza we wszystkich dodatkach VSTO programu Outlook. Nie można zmienić wartości `Microsoft.Office.Tools.Outlook.FormRegionName` atrybutu poprzez zmianę nazwy elementu regionu formularza lub przez zmianę <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> właściwości. Aby zmienić tę nazwę, należy zmodyfikować `Microsoft.Office.Tools.Outlook.FormRegionName` atrybut w pliku kodu regionu formularza.|

## <a name="disable-form-region-inheritance"></a><a name="DisablingInheritance"></a> Wyłącz dziedziczenie regionów formularza
 Domyślnie Klasa komunikatów niestandardowych dziedziczy wszystkie skojarzenia regionów formularzy podstawowej klasy komunikatów. Na przykład Klasa komunikatu o nazwie `IPM.Task.Contoso` dziedziczy z `IPM.Task` . W związku z tym `IPM.Task.Contoso` dziedziczy skojarzenia regionu formularza `IPM.Task` .

 Jeśli nie chcesz, aby region formularza został skojarzony z żadną pochodną klasą komunikatów, ustaw <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> Właściwość region formularza na **wartość true**. Na przykład, jeśli skojarzesz sąsiedni region formularza z `IPM.Task` i ustawisz <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> Właściwość na **true**, region formularza zostanie dołączony tylko do dolnej części standardowego formularza zadania. Region formularza nie zostanie dołączony do dolnej części dowolnych dostosowanych wersji standardowego formularza zadania.

## <a name="understand-types-and-message-class-names"></a><a name="ClassNames"></a> Opis typów i nazw klas komunikatów
 Nazwa typu elementu programu Outlook różni się od nazwy klasy wiadomości elementu programu Outlook. Na przykład nazwa typu elementu RSS to `Microsoft.Office.Interop.Outlook.PostItem` . Nazwa klasy wiadomości elementu RSS to `IPM.Post.RSS` .

 Użyj nazwy typu, aby odwołać się do elementu programu Outlook w kodzie. Aby uzyskać listę nazw typów, zobacz [kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

 Użyj nazwy klasy wiadomości elementów programu Outlook w kreatorze **nowego regionu formularza programu Outlook** w celu skojarzenia elementu z regionem formularza. Aby uzyskać listę prawidłowych nazw klas komunikatów, zobacz [kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="design-adjoining-form-regions-for-the-reading-pane"></a><a name="ReadingPane"></a> Projektuj przylegające obszary formularzy dla okienka odczytu
 Możesz użyć okienka czytania programu Outlook, aby wyświetlić podgląd elementu programu Outlook bez otwierania elementu. Okienko odczytu jest przeznaczone tylko do odczytu. W związku z tym, formanty wejściowe, które można dodać do sąsiadującego regionu formularza, takie jak pole tekstowe, mogą nie zachowywać się zgodnie z oczekiwaniami, gdy region elementu i formularza jest otwarty w okienku odczytywania.

 Na przykład jeśli element, który ma sąsiadujący region formularza jest otwarty w okienku odczytywania, możliwe jest następujące sytuacje:

1. Zaznacz tekst w polu tekstowym, które znajduje się w regionie formularza.

2. Naciśnij klawisz **delete**.

3. Cały element poczty jest usuwany zamiast tekstu w polu tekstowym.

   Jeśli projektujesz sąsiadujący region formularza zawierający kontrolki wejściowe, przetestuj kontrolki w okienku odczytywania, aby upewnić się, że działają prawidłowo. Rozważ dodanie niestandardowego kodu, który wyłącza kontrolki, które nie zachowywać się zgodnie z oczekiwaniami.

   Alternatywnie można ustawić <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> Właściwość region formularza na **wartość false**. W ten sposób region formularza nie może być używany w okienku odczytywania.

## <a name="use-optimal-icon-sizes"></a><a name="UsingOptimal"></a> Użyj optymalnych rozmiarów ikon
 Możesz określić, które ikony mają być wyświetlane w regionie formularza przez ustawienie właściwości ikony w grupie właściwości **ikony** okna **Właściwości** . Poniższe wskazówki umożliwiają osiągnięcie najlepszej jakości wizualnej:

- Dla ikony **strony** użyj pliku Portable Network Graphics (PNG).

- Ikony **okna** powinny zawierać od 32 do 32 pikseli.

- Wszystkie inne ikony powinny mieć 16 pikseli na 16 pikseli.

  Ikona **strony** pojawia się na Wstążce inspektora dla elementów, które mają oddzielne, zastępcze lub zastąpione regiony formularzy.

  Ikona **okna** jest wyświetlana w obszarze powiadomień, a w oknie dialogowym **Alt** + **Tab** dla otwartych elementów wyświetlających zastępowanie lub zastępowanie — wszystkie regiony formularza.

## <a name="see-also"></a>Zobacz też
- [Dostęp do regionu formularza w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Przewodnik: Projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
