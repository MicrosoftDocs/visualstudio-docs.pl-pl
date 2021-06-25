---
title: Pobieranie informacji o usłudze z magazynu ustawień | Microsoft Docs
description: Dowiedz się, jak za pomocą magazynu ustawień znaleźć wszystkie dostępne usługi lub określić, czy jest zainstalowana określonej usługi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb014803945ea88cd6c2c27eee8c120059014a18
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900645"
---
# <a name="get-service-information-from-the-settings-store"></a>Uzyskiwanie informacji o usłudze z magazynu ustawień
Magazyn ustawień umożliwia znalezienie wszystkich dostępnych usług lub określenie, czy jest zainstalowana określonej usługi. Musisz znać typ klasy usługi.

## <a name="to-list-the-available-services"></a>Aby wyświetlić listę dostępnych usług

1. Utwórz projekt VSIX o nazwie `FindServicesExtension` , a następnie dodaj polecenie niestandardowe o nazwie `FindServicesCommand` . Aby uzyskać więcej informacji na temat tworzenia polecenia niestandardowego, zobacz Create an extension with a menu command (Tworzenie [rozszerzenia za pomocą polecenia menu).](../extensibility/creating-an-extension-with-a-menu-command.md)

2. W *findServicesCommand.cs*, dodaj następujące dyrektywy using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Pobierz magazyn ustawień konfiguracji, a następnie znajdź podkolekcję o nazwie Services. Ta kolekcja zawiera wszystkie dostępne usługi. W metodzie usuń istniejący kod i `MenuItemCommand` zastąp go następującym kodem:

    ```csharp
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

4. Skompilowanie projektu i rozpoczęcie debugowania. Zostanie wyświetlone wystąpienie eksperymentalne.

5. W wystąpieniu eksperymentalnym w menu **Narzędzia** kliknij polecenie **Wywołaj polecenie ZnajdźUsługiCommand.**

     Powinno zostać wyświetlony komunikat z listą wszystkich usług.

     Aby sprawdzić te ustawienia, możesz użyć edytora rejestru.

## <a name="find-a-specific-service"></a>Znajdowanie określonej usługi
 Można również użyć metody <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> , aby określić, czy jest zainstalowana określonej usługi. Musisz znać typ klasy usługi.

1. W menuItemCallback projektu utworzonego w poprzedniej procedurze wyszukaj w magazynie ustawień konfiguracji kolekcję z podkolekcją o nazwie guid `Services` usługi. W tym przypadku poszukamy usługi Pomocy.

    ```csharp
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

2. Skompilowanie projektu i rozpoczęcie debugowania.

3. W wystąpieniu eksperymentalnym w menu **Narzędzia** kliknij polecenie **Wywołaj polecenie ZnajdźUsługiCommand.**

     Powinien zostać wyświetlony komunikat z tekstem **Help Service Available (Dostępna usługa pomocy):** true **(prawda) lub** false **(fałsz).** Aby sprawdzić to ustawienie, możesz użyć edytora rejestru, jak pokazano we wcześniejszych krokach.
