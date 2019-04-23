---
title: Pobieranie informacji o usłudze z Store ustawienia | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfe754203ae9b4e951de5beef8cd829f9d7716bb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116657"
---
# <a name="getting-service-information-from-the-settings-store"></a>Pobieranie informacji o usłudze z magazynu ustawień
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można użyć magazynu ustawień, aby znaleźć wszystkie dostępne usługi lub aby określić, czy określona usługa jest zainstalowana. Musisz znać typ klasy usługi.  
  
### <a name="to-list-the-available-services"></a>Aby wyświetlić listę dostępnych usług  
  
1. Utwórz projekt VSIX o nazwie FindServicesExtension, a następnie dodaj polecenie niestandardowe o nazwie FindServicesCommand. Aby uzyskać więcej informacji na temat tworzenia niestandardowych poleceń, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2. W FindServicesCommand.cs, Dodaj następujące instrukcje using:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3. Pobierz magazyn ustawień konfiguracji, a następnie znajdź podkolekcję o nazwie usługi. Ta kolekcja zawiera wszystkie dostępne usługi. W metodzie MenuItemCommand Usuń istniejący kod i zastąp go następujące czynności:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string message = "Available services:\n";  
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");  
        int n = 0;  
        foreach (string service in collection)  
        {  
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";  
        }  
  
        MessageBox.Show(message);  
    }  
    ```  
  
4. Skompiluj projekt, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.  
  
5. W doświadczalnym wystąpieniu na **narzędzia** menu, kliknij przycisk **wywołania FindServicesCommand**.  
  
     Okno komunikatu, wyświetlanie listy wszystkich usług powinny być widoczne.  
  
     Aby sprawdzić te ustawienia, można Użyj Edytora rejestru.  
  
## <a name="finding-a-specific-service"></a>Wyszukiwanie w określonych usługach  
 Można również użyć <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> metodę pozwala ustalić, czy określona usługa jest zainstalowana. Musisz znać typ klasy usługi.  
  
1. Wyszukaj w sklepie ustawień konfiguracji w MenuItemCallback projekt utworzony w poprzedniej procedurze, `Services` kolekcja, która ma podkolekcję o nazwie określonej przez identyfikator GUID usługi. W takim przypadku firma Microsoft będzie szukał usługi pomocy.  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();  
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);  
        string message = "Help Service Available: " + hasHelpService;  
  
        MessageBox.Show(message);  
    }  
    ```  
  
2. Skompiluj projekt, a następnie rozpocząć debugowanie.  
  
3. W doświadczalnym wystąpieniu na **narzędzia** menu, kliknij przycisk **wywołania FindServicesCommand**.  
  
     Powinien zostać wyświetlony komunikat z tekstem **pomocy dostępne usługi:** następuje **True** lub **False**. Aby sprawdzić to ustawienie, służy Edytor rejestru, jak pokazano w poprzednich krokach.
