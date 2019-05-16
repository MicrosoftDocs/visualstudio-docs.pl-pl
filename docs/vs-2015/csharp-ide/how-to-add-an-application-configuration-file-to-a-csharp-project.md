---
title: 'Instrukcje: Dodawanie pliku konfiguracji aplikacji do C# projektu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bc5c8dbad4d2bb248a3183e2e73d7c2932e7bce4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681727"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Instrukcje: Dodawanie pliku konfiguracji aplikacji do C# projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przez dodawanie pliku konfiguracji aplikacji (plik app.config) do projektu C#, można dostosować, jak środowisko uruchomieniowe języka wspólnego lokalizuje i ładuje pliki zestawu. Aby uzyskać więcej informacji o plikach konfiguracji aplikacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
> [!NOTE]
> Nie obsługuje Store Windows <xref:System.Configuration>. Z tego powodu Store apps nie zawierają szablonu pliku app.config.  
  
 Podczas tworzenia projektu środowiska programistycznego automatycznie kopiuje plik app.config, zmienia nazwę pliku kopiowania, aby dopasować plik wykonywalny i przenosi kopii w katalogu bin.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Aby dodać plik konfiguracji aplikacji do projektu C#  
  
1. Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
     **Dodaj nowy element** pojawi się okno dialogowe.  
  
2. Rozwiń **zainstalowane**, rozwiń węzeł **elementy Visual C#**, a następnie wybierz **pliku konfiguracji aplikacji** szablonu.  
  
3. W **nazwa** polu tekstowym wprowadź nazwę, a następnie wybierz **Dodaj** przycisku.  
  
     Plik, który nosi nazwę pliku app.config zostanie dodany do projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie ustawieniami aplikacji (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Schemat pliku konfiguracji](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [Konfigurowanie aplikacji](https://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f)   
 [Instrukcje: Konfigurowanie aplikacji pod kątem określonej wersji oprogramowania .NET Framework](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Używanie środowiska programistycznego Visual Studio dla C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)