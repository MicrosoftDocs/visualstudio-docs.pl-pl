---
title: Pobieranie informacji o usłudze z magazynu ustawień | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfe754203ae9b4e951de5beef8cd829f9d7716bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204313"
---
# <a name="getting-service-information-from-the-settings-store"></a>Pobieranie informacji o usłudze z magazynu ustawień
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby znaleźć wszystkie dostępne usługi lub określić, czy dana usługa jest zainstalowana, można użyć magazynu ustawień. Musisz znać typ klasy usługi.  
  
### <a name="to-list-the-available-services"></a>Aby wyświetlić listę dostępnych usług  
  
1. Utwórz projekt VSIX o nazwie FindServicesExtension, a następnie dodaj polecenie niestandardowe o nazwie FindServicesCommand. Aby uzyskać więcej informacji na temat tworzenia polecenia niestandardowego, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2. W FindServicesCommand.cs Dodaj następujące instrukcje using:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3. Pobierz magazyn ustawień konfiguracji, a następnie Znajdź podkolekcję o nazwie Services. Ta kolekcja zawiera wszystkie dostępne usługi. W metodzie MenuItemCommand usuń istniejący kod i zastąp go następującym:  
  
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
  
4. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.  
  
5. W eksperymentalnym wystąpieniu, w menu **Narzędzia** kliknij polecenie **Wywołaj FindServicesCommand**.  
  
     Powinien pojawić się okno komunikatu z listą wszystkich usług.  
  
     Aby sprawdzić te ustawienia, można użyć Edytora rejestru.  
  
## <a name="finding-a-specific-service"></a>Znajdowanie określonej usługi  
 Można również użyć metody, <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> Aby określić, czy dana usługa jest zainstalowana. Musisz znać typ klasy usługi.  
  
1. W MenuItemCallback projektu, który został utworzony w poprzedniej procedurze, Wyszukaj w magazynie ustawienia konfiguracji `Services` kolekcję, która ma podkolekcję o nazwie identyfikator GUID usługi. W takim przypadku będziemy szukać usługi pomocy.  
  
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
  
2. Skompiluj projekt i Rozpocznij debugowanie.  
  
3. W eksperymentalnym wystąpieniu, w menu **Narzędzia** kliknij polecenie **Wywołaj FindServicesCommand**.  
  
     Powinien zostać wyświetlony komunikat z **dostępną usługą**  tekstową: po której następuje **wartość true** lub **false**. Aby sprawdzić to ustawienie, można użyć Edytora rejestru, jak pokazano w poprzednich krokach.
