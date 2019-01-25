---
title: Programowanie zespołowe rozwiązań pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 897b90c9b370d61cfe8f3202e0f3c5c33ce6f613
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875969"
---
# <a name="collaborative-development-of-office-solutions"></a>Programowanie zespołowe rozwiązań pakietu Office
  Wielu deweloperów pracować w projekcie programu pakietu Office w taki sam sposób, jak współpracują w innych projektów programu Visual Studio. Program Visual Studio poprawnie lokalizuje instalacji pakietu Microsoft Office, na każdym komputerze, nawet jeśli Office jest zainstalowana w różnych lokalizacjach. Istnieją jednak pewne istotne kwestie, w których trzeba pamiętać.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>Debugowanie właściwości nie są współdzielone.  
 Debugowanie właściwości nie są współużytkowane przez wielu użytkowników pod kontrolą źródła. Visual Basic i Visual C# projektów zapisanie właściwości debugowania w pliku specyficzne dla użytkownika (*ProjectName*. vbproj.user lub *ProjectName*. csproj.user), a ten plik nie jest pod kontrolą źródła . Jeśli debugowanie jest więcej niż jedna osoba, każda osoba właściwości debugowania ręcznie wprowadzić.  
  
 Jeśli projekt jest przechowywane w udziale sieciowym, zamiast w kontroli źródła, kilka dodatkowych kroków należy włączyć współpracujących deweloperów otworzyć rozwiązanie i przetestować zestaw.  
  
## <a name="source-control-requires-checking-out-all-files"></a>Kontrola źródła wymaga wyewidencjonowywanie wszystkie pliki  
 Jeśli używasz kontroli źródła dla projektów, należy sprawdzić wszystkie pliki w pliku z kodem w **Eksploratora rozwiązań** (takie jak *ThisDocument*, *ThisWorkbook*, lub *ThisAddIn* pliki z kodem) za każdym razem, gdy zmienisz plik kodu, nawet plików, które są domyślnie ukryte. Jeśli należy wyewidencjonować plik kodu najwyższego poziomu, zmiany mogą zostać utracone.  
  
 Po dokonaniu zmian, sprawdź, czy wszystkie pliki z powrotem w. Aby uzyskać więcej informacji na temat plików ukrytych kodu w projektach, zobacz [projekty pakietu Office w środowisku Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>Zabezpieczenia nieformalne współpracy w sieci  
 Dla wszystkich rozwiązań poziomie dokumentu, które znajdują się w lokalizacji sieciowej (takie jak \\ \\ *Servername*\\*Sharename*), w pełni kwalifikowanej lokalizacji musi zostać dodany do Lista zaufanych folderu w aplikacji Microsoft Office, który aktualnie pracuje. Wybierz opcję, aby dołączyć podkatalogów w folderze głównym lub specjalnie dodać debugowania i tworzyć foldery do listy zaufanych folderów. Aby uzyskać więcej informacji na temat jak to zrobić, zobacz [udzielenia zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  
  
 Tymczasowe certyfikaty, które są automatycznie generowane w czasie kompilacji nie są zabezpieczane przez hasła. Certyfikaty zawierają nazwę logowania dla deweloperów i innych danych osobowych. W przypadku wdrożenia dostosowania, które są podpisane przez certyfikaty tymczasowe innych może być mogli korzystać z tych informacji.  
  
## <a name="see-also"></a>Zobacz także  
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)  
