---
title: 'Instrukcje: Ponowne włączanie dodatku VSTO, który został wyłączony'
description: Dowiedz się, jak za pomocą programu Visual Studio ponownie włączyć dodatek Narzędzia VSTO, który został wyłączony w aplikacji Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: de3e251c15699ce29b7986e4f0cc19a3f5c5798d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942193"
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Instrukcje: Ponowne włączanie dodatku VSTO, który został wyłączony
  Aplikacje Microsoft Office mogą wyłączyć dodatki VSTO, które zachowywać się nieoczekiwanie. Jeśli aplikacja nie ładuje dodatku VSTO podczas próby debugowania, aplikacja mogła zostać trwale wyłączona lub nie wyłączyła dodatku VSTO.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="hard-disabled-vsto-add-ins"></a>Twarde dodatki narzędzi VSTO
 Twarde wyłączenie może wystąpić, gdy dodatek VSTO powoduje nieoczekiwane zamknięcie aplikacji. Może również wystąpić na komputerze deweloperskim, jeśli zostanie zatrzymany debuger podczas <xref:Microsoft.Office.Tools.AddIn.Startup> wykonywania programu obsługi zdarzeń w dodatku VSTO.

### <a name="to-re-enable-a-vsto-add-in"></a>Aby ponownie włączyć dodatek narzędzi VSTO

1. W aplikacji kliknij kartę **plik** .

2. Kliknij przycisk  **Opcje** ApplicationName.

3. W okienku kategorie kliknij pozycję **Dodatki**.

4. W okienku szczegółów sprawdź, czy dodatek VSTO pojawia się na liście **wyłączone dodatki aplikacji** .

     Kolumna **name** określa nazwę zestawu, a kolumna **Location** określa pełną ścieżkę manifestu aplikacji.

5. W polu **Zarządzaj** kliknij pozycję **Wyłączone elementy**, a następnie kliknij pozycję **Przejdź**.

6. Wybierz dodatek VSTO, a następnie kliknij pozycję **Włącz**.

7. Kliknij przycisk **Zamknij**.

## <a name="soft-disabled-vsto-add-ins"></a>Nietrwałe dodatki narzędzi VSTO
 Wyłączenie nietrwałe może wystąpić, gdy dodatek VSTO generuje błąd, który nie powoduje nieoczekiwanego zamknięcia aplikacji. Na przykład aplikacja może uniemożliwić wyłączenie dodatku VSTO, jeśli zgłasza nieobsługiwany wyjątek podczas <xref:Microsoft.Office.Tools.AddIn.Startup> wykonywania programu obsługi zdarzeń.

> [!NOTE]
> Po ponownym włączeniu dodatku narzędzi VSTO wyłączonego przez program Aplikacja natychmiast podejmie próbę załadowania dodatku VSTO. Jeśli problem, który początkowo spowodował nieprzerwane wyłączenie przez aplikację dodatku VSTO, nie został usunięty, aplikacja spowoduje ponowne wyłączenie dodatku VSTO.

### <a name="to-re-enable-a-vsto-add-in"></a>Aby ponownie włączyć dodatek narzędzi VSTO

1. W aplikacji kliknij kartę **plik** .

2. Kliknij przycisk  **Opcje** ApplicationName.

3. W okienku kategorie kliknij pozycję **Dodatki**.

4. W okienku szczegółów sprawdź, czy dodatek VSTO pojawia się na liście **dodatków nieaktywnej aplikacji** .

     Kolumna **name** określa nazwę zestawu, a kolumna **Location** określa pełną ścieżkę manifestu aplikacji.

5. W oknie **Zarządzanie** kliknij pozycję **Dodatki COM**, a następnie kliknij pozycję **Przejdź**.

6. W oknie dialogowym **Dodatki COM** zaznacz pole wyboru obok wyłączonego dodatku narzędzi VSTO.

7. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Debugowanie projektów pakietu Office](../vsto/debugging-office-projects.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
