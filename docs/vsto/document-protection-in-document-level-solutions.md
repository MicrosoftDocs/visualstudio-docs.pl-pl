---
title: Ochrona dokumentów w rozwiązaniach na poziomie dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 03724e523c1f49277e0bc2b23465d5296d806695
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648538"
---
# <a name="document-protection-in-document-level-solutions"></a>Ochrona dokumentów w rozwiązaniach na poziomie dokumentu
  Można użyć funkcji ochrony programu Microsoft Office Word i Microsoft Office Excel w projektach na poziomie dokumentu. Te funkcje blokują użytkowników nieautoryzowanych możliwość wprowadzania zmian na chronionych części dokumentu.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Za pomocą programu Excel, można włączyć ochrony włączać i wyłączać podczas, gdy skoroszyt jest otwarty w projektancie. Korzystając z programu Word, można włączyć ochrony tylko poza projektanta. W czasie wykonywania można włączyć lub wyłączyć ochronę programowe dla programu Word i Excel.  
  
 Po włączeniu ochrony dokumentu do dokumentu, który jest otwarty w Projektancie wszystkich kontrolek zostaną usunięte z **przybornika** lub stają się dostępne, i nie można przeciągnąć niczego z **źródeł danych** okno w dokumencie.  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument i chronione dokumenty  
 Jeśli dokument jest chroniony, pamięć podręczną danych nie są dostępne poza dokumentu. Nie można użyć <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy do pobrania i modyfikować dane, które są buforowane w chronionym dokumencie lub zastosowanie innych metod <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> klasy.  
  
## <a name="word-document-protection-in-the-designer"></a>Ochrona dokumentu programu Word w Projektancie  
 Jeśli dodasz ochrony do dokumentu programu Word lub szablonu, gdy jest on otwarty w programie Visual Studio, nie można rozpocząć Wymuszanie ochrony w projektancie. Dokument jest w trybie projektowania, gdy jest on otwarty w programie Visual Studio, a jego musi być w trybie uruchamiania przed rozpoczęciem wymuszania ochrony.  
  
 Jeśli tworzysz projekt, który korzysta z istniejącego dokumentu programu Word, który ma włączoną ochronę, dokument jest chroniony otwarty w projektancie. Nie można edytować chronionych części dokumentu, ale można nadal napisać kod, aby zautomatyzować dokumentu w edytorze kodu. Możesz również nie można skompilować projekt po włączeniu ochrony, gdy dokument jest otwarty w programie Visual Studio.  
  
 Można wyłączyć ochrony, gdy dokument jest otwarty w projektancie, dzięki czemu mogą edytować dokument i skompiluj projekt. Nie można wyłączyć ochrony dla kopii w projektancie, podczas debugowania; dokument, który zostanie otwarty podczas debugowania jest oddzielna kopia z jednego otwartym w Projektancie (Kopiuj dane wyjściowe są przechowywane w *\bin* katalogu dla języka Visual Basic i *\bin\debug* katalog dla C# ).  
  
 Można włączyć ochrony na kopię dokumentu, który zostanie otwarty w projektancie, zamknięcie projektu w programie Visual Studio, otwierając kopię dokumentu, który znajduje się w katalogu projektu i włączając ochronę.  
  
## <a name="enforce-word-document-protection-on-build"></a>Wymuszanie ochrony dokumentu programu Word w kompilacji  
 Program Visual Studio uruchamia wymuszania ochrony dokumentów programu Word i szablony w procesie kompilacji, ochrona jest włączona, po otwarciu dokumentu do debugowania. Dokument jest chroniony przy użyciu pustego hasła.  
  
 Ochrona jest włączane podczas kompilacji tak, jeśli istnieje kod w dokumencie <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzenia, które mogą spowodować, że wyjątki lub zmienić zachowanie aplikacji, ten kod może być debugowany poprawnie. Po włączeniu ochrony po otwarciu dokumentu, kod inicjujący nie można debugować lub testowana.  
  
## <a name="setting-the-password"></a>Ustawianie hasła  
 Visual Studio automatycznie włącza ochronę, ale domyślnie udostępnia bez hasła. Jeśli chcesz ochrony dokumentu jest hasło, należy dodać przed wdrożeniem rozwiązania. Dodanie hasła, umożliwia zezwala autoryzowanym użytkownikom usuwanie ochrony z dokumentu. bez hasła nie można łatwo usunąć ochrony. Aby uzyskać szczegółowe informacje o ustawianiu hasła Zobacz Pomoc w określonej aplikacji pakietu Office.  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Programowe Włączanie ochrony dokumentów i części dokumentów](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Office development ― przykłady i przewodniki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Zarządzanie prawami do informacji i przegląd rozszerzeń kodu zarządzanego](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Ochrona za pomocą hasła w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)   
 [Instrukcje: Zezwalanie kodu do uruchamiania w tle dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)  
  
  