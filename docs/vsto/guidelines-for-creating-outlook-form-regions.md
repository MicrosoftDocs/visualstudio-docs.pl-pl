---
title: Wytyczne dotyczące tworzenia regionów formularzy programu Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: d2a052cbad69f87c5b25005ff21959841af55f68
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648758"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Wytyczne dotyczące tworzenia regionów formularzy programu Outlook
  Poniższe informacje mogą pomóc w optymalizacji regionów formularzy w sieci i uniknąć potencjalnych problemów:  
  
- [Użyj nazwy regionu formularza](#UsingFormRegions).  
  
- [Wyłącz dziedziczenie regionu formularza](#DisablingInheritance).  
  
- [Informacje o typach i nazwy klas wiadomości](#ClassNames).  
  
- [Projektowanie regionów formularzy w okienku odczytu sąsiadujące](#ReadingPane).  
  
- [Użyj rozmiarów optymalnych ikonę](#UsingOptimal).  
  
  Aby uzyskać więcej informacji na temat regionów formularzy zobacz [regionach formularzy programu Outlook z tworzenia](../vsto/creating-outlook-form-regions.md).  
  
  [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
##  <a name="UsingFormRegions"></a> Użyj nazwy regionów formularza  
 Istnieje kilka nazw używany do opisania regionu formularza. Należy zrozumieć różnicę między te nazwy i ich wpływ na region formularza. W poniższej tabeli opisano nazwy.  
  
|Nazwa regionu formularza|Opis|  
|----------------------|-----------------|  
|Nazwa elementu regionu formularza|Nazwa określona dla **Region formularza programu Outlook** pozycja **Dodaj nowy element** okno dialogowe. Jest to nazwa pliku kodu regionu formularza, który pojawia się w **Eksploratora rozwiązań**.|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> Właściwość|Określ tę nazwę w **tekst opisu i wybierz preferencje wyświetlania** strony **nowy Region formularza programu Outlook** kreatora. Ta nazwa jest wyświetlana jako **FormRegionName** właściwość **właściwości** okna.<br /><br /> Użyj <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> właściwości w celu określenia etykietę, która identyfikuje region formularza programu Outlook interfejsu użytkownika (UI). Dla regionów formularza oddzielny ta nazwa jest wyświetlana jako przycisk na Wstążce elementu programu Outlook.<br /><br /> Dla regionów formularza sąsiednimi ta nazwa pojawia się jako tekst nagłówka powyżej regionu formularza.|  
|`Microsoft.Office.Tools.Outlook.FormRegionName` Atrybut|Po dodaniu **Region formularza programu Outlook** elementu do projektu, program Visual Studio ustawia tę właściwość, aby w pełni kwalifikowaną nazwę regionu formularza. W pełni kwalifikowana nazwa domyślna jest nazwa dodatku narzędzi VSTO połączona nazwa regionu formularza za pomocą pojedynczego znaku kropki — na przykład `OutlookAddIn1.FormRegion1`.<br /><br /> Ta w pełni kwalifikowana nazwa pojawia się również jako atrybut u góry klasy fabryka regionów formularza.<br /><br /> Użyj `Microsoft.Office.Tools.Outlook.FormRegionName` atrybutu, aby jednoznacznie zidentyfikować region formularza we wszystkich dodatków narzędzi VSTO dla programu Outlook. Nie można zmienić wartość `Microsoft.Office.Tools.Outlook.FormRegionName` atrybutu, zmieniając element regionu formularza lub zmieniając <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> właściwości. Aby zmienić tę nazwę, należy zmodyfikować `Microsoft.Office.Tools.Outlook.FormRegionName` atrybutu w pliku kodu regionu formularza.|  
  
##  <a name="DisablingInheritance"></a> Wyłącz dziedziczenie regionu formularza  
 Domyślnie niestandardową klasę wiadomości dziedziczy wszystkie skojarzenia regionu formularza klasy bazowej wiadomości. Na przykład o nazwie klasy wiadomości `IPM.Task.Contoso` pochodzi od klasy `IPM.Task`. W związku z tym `IPM.Task.Contoso` dziedziczy formularza skojarzenia region `IPM.Task`.  
  
 Jeśli użytkownik nie chce region formularza ma być skojarzona z wszystkie pochodne klasy wiadomości, ustaw <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> właściwość regionu formularza **true**. Na przykład w przypadku skojarzenia sąsiednimi regionu formularza z `IPM.Task` i ustaw <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> właściwości **true**, region formularza tylko zostaną dołączone do dołu formularza zadania standardowego. Region formularza nie zostanie dołączony do dołu wszystkie wersje dostosowany formularz zadania standardowego.  
  
##  <a name="ClassNames"></a> Opis typów i nazwy klas wiadomości  
 Nazwa typu elementu programu Outlook różni się od nazwy klas wiadomości, elementu programu Outlook. Na przykład, nazwa typu elementu danych RSS jest `Microsoft.Office.Interop.Outlook.PostItem`. Nazwa klasy wiadomości elementu danych RSS jest `IPM.Post.RSS`.  
  
 Użyj nazwy typu można odwoływać się do elementu programu Outlook w kodzie. Aby uzyskać listę nazw typów, zobacz [kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
 Użyj nazwy klas wiadomości elementów programu Outlook w **nowy Region formularza programu Outlook** kreatora, aby skojarzyć element z regionu formularza. Aby uzyskać listę nazw klas prawidłowy komunikat, zobacz [kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
##  <a name="ReadingPane"></a> Projektowanie regionów formularzy w przylegającym okienka odczytu  
 W okienku odczytu programu Outlook umożliwia elementu programu Outlook w wersji zapoznawczej bez konieczności otwierania elementu. W okienku odczytu jest przeznaczony do odczytu tylko. W związku z tym, kontrolki wejściowe, które dodajesz do regionów formularzy programu sąsiadujących, takich jak pole tekstowe, mogą nie zachowywać się zgodnie z oczekiwaniami, gdy region elementu i formularz są otwarte w okienku odczytu.  
  
 Na przykład jeśli element, który ma przylegającym regionie formularza jest otwarty w okienku odczytu, możliwe jest następujących sytuacji:  
  
1. W polu tekstowym, która znajduje się na region formularza, zaznacz jakiś tekst.  
  
2. Naciśnij klawisz **Usuń**.  
  
3. Element całego poczty zostanie usunięty zamiast tekstu w polu tekstowym.  
  
   W przypadku projektowania sąsiednimi regionu formularza, który zawiera kontrolki wejściowe, przetestuj kontrolki w okienku odczytu, aby upewnić się, że działają prawidłowo. Rozważ dodanie kodu niestandardowego, który wyłącza formantów, które nie zachowywać się zgodnie z oczekiwaniami.  
  
   Alternatywnie, można ustawić <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> właściwość regionu formularza **False**. Nie można używać w ten sposób regionu formularza w okienku odczytu.  
  
##  <a name="UsingOptimal"></a> Użyj rozmiarów optymalnych ikony  
 Można określić, ikony, które mają być regionu formularza do wyświetlenia przez ustawienie właściwości ikony w **ikony** grupy właściwości **właściwości** okna. Aby osiągnąć najwyższą jakość wizualną, skorzystaj z poniższych wskazówek:  
  
- Aby uzyskać **strony** ikonę, przy użyciu pliku Portable Network Graphics (PNG).  
  
- **Okno** ikon powinna być 32 x 32 piksele.  
  
- Wszystkie inne ikony powinien być 16 x 16 pikseli.  
  
  **Strony** pojawi się ikona na Wstążce Inspektor dla elementów, które mają oddzielny, zamieniania lub regionów formularza Zamień wszystkie.  
  
  **Okna** ikona pojawia się w obszarze powiadomień, a następnie w **Alt**+**kartę** okno dialogowe Otwórz elementy tego wyświetlana zastąpienia lub formularza Zamień wszystkie regiony.  
  
## <a name="see-also"></a>Zobacz także  
 [Dostęp do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Przewodnik: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  