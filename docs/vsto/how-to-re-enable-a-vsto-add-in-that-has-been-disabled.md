---
title: 'Instrukcje: Ponowne włączanie dodatku narzędzi VSTO dla programów, która została wyłączona'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: adcfab22ea9f6acc9c75f59fa17127cab348fc37
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939401"
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Instrukcje: Ponowne włączanie dodatku narzędzi VSTO dla programów, która została wyłączona
  Aplikacje Microsoft Office może spowodować wyłączenie dodatków narzędzi VSTO dla programów, które nieoczekiwane zachowanie. Jeśli aplikacja nie można załadować dodatku narzędzi VSTO dla programów podczas próby debugowania aplikacji może być twardych wyłączone lub wyłączone nietrwałego dodatku narzędzi VSTO dla programów.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="hard-disabled-vsto-add-ins"></a>Dodatków narzędzi VSTO twardych wyłączone  
 Wyłączanie ciężko może wystąpić, gdy dodatku narzędzi VSTO powoduje, że aplikacja jest nieoczekiwanie zamykany. Go może również wystąpić na komputerze deweloperskim po zatrzymaniu debugera podczas <xref:Microsoft.Office.Tools.AddIn.Startup> wykonywania obsługi zdarzeń w dodatku VSTO.  
  
### <a name="to-re-enable-a-vsto-add-in"></a>Aby ponownie włączyć funkcję dodatku narzędzi VSTO  
  
1.  W aplikacji, kliknij przycisk **pliku** kartę.  
  
2.  Kliknij przycisk *ApplicationName* **opcje** przycisku.  
  
3.  W okienku kategorii kliknij **Add-ins**.  
  
4.  W okienku szczegółów, sprawdź, czy dodatku narzędzi VSTO znajduje się w **aplikacji wyłączonych dodatków** listy.  
  
     **Nazwa** kolumnie Określa nazwę zestawu, a **lokalizacji** kolumnie Określa pełną ścieżkę manifestu aplikacji.  
  
5.  W **Zarządzaj** kliknij **elementy wyłączone**, a następnie kliknij przycisk **Przejdź**.  
  
6.  Wybierz dodatek narzędzi VSTO dla programów, a następnie kliknij przycisk **Włącz**.  
  
7.  Kliknij przycisk **Zamknij**.  
  
## <a name="soft-disabled-vsto-add-ins"></a>Dodatków narzędzi VSTO nietrwałego — wyłączone  
 Wyłączanie nietrwałego może wystąpić, gdy dodatku narzędzi VSTO generuje błąd, który nie powoduje nieoczekiwanego zamknięcia aplikacji. Na przykład aplikacja nietrwałe może wyłączyć dodatku narzędzi VSTO dla programów, jeśli wyniku weryfikacji zgłasza wyjątek nieobsługiwany wyjątek podczas <xref:Microsoft.Office.Tools.AddIn.Startup> programu obsługi zdarzeń jest wykonywany.  
  
> [!NOTE]  
>  Po ponownym włączeniu dodatku narzędzi VSTO wyłączone nietrwałego aplikacji natychmiast próbuje załadować dodatku narzędzi VSTO. Jeśli nie został rozwiązany problem powodujący początkowo aplikacji nietrwałego wyłączenia dodatku narzędzi VSTO dla programów, aplikacja będzie nietrwałe ponownie go wyłączyć dodatku narzędzi VSTO.  
  
### <a name="to-re-enable-a-vsto-add-in"></a>Aby ponownie włączyć funkcję dodatku narzędzi VSTO  
  
1.  W aplikacji, kliknij przycisk **pliku** kartę.  
  
2.  Kliknij przycisk *ApplicationName* **opcje** przycisku.  
  
3.  W okienku kategorii kliknij **Add-ins**.  
  
4.  W okienku szczegółów, sprawdź, czy dodatku narzędzi VSTO znajduje się w **dodatki aplikacji nieaktywne** listy.  
  
     **Nazwa** kolumnie Określa nazwę zestawu, a **lokalizacji** kolumnie Określa pełną ścieżkę manifestu aplikacji.  
  
5.  W **Zarządzaj** kliknij **dodatki COM**, a następnie kliknij przycisk **Przejdź**.  
  
6.  W **dodatki COM** okno dialogowe, zaznacz pole wyboru obok wyłączonego dodatku narzędzi VSTO.  
  
7.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz także  
 [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Debugowanie projektów pakietu Office](../vsto/debugging-office-projects.md)   
 [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)  
