---
title: Jak opublikować projekt, który ma określone ustawienia regionalne | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, localized projects
- locales, publishing for
- deploying applications [ClickOnce], localized projects
- locales, deploying for
- publishing localized projects
- macros, deploying with
- macros, publishing with
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d3b3aa7c2c56b1175c2f280a96ade78ea17ee55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382227"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Instrukcje: publikowanie projektu, który ma określone ustawienia regionalne
Aplikacja zawiera składniki, które mają różne ustawienia regionalne. W tym scenariuszu należy utworzyć rozwiązanie, które ma kilka projektów, a następnie opublikować oddzielne projekty dla każdego ustawienia regionalnego. Ta procedura pokazuje, jak użyć makra do opublikowania pierwszego projektu w rozwiązaniu przy użyciu ustawień regionalnych "en". Jeśli chcesz wypróbować tę procedurę przy użyciu ustawień regionalnych innych niż "en", upewnij się, że ustawienie `localeString` w makrze jest zgodne z ustawieniami regionalnymi, które są używane (na przykład "de" lub "de-de").

> [!NOTE]
> W przypadku korzystania z tego makra lokalizacja publikowania powinna być prawidłowym adresem URL lub Universal Naming Convention (UNC). Na komputerze należy również zainstalować Internet Information Services (IIS). Aby zainstalować usługi IIS, w menu **Start** kliknij pozycję **Panel sterowania**. Kliknij dwukrotnie ikonę **Dodaj lub usuń programy**. W oknie **Dodawanie lub usuwanie programów**kliknij pozycję **Dodaj/Usuń składniki systemu Windows**. W **Kreatorze składników systemu Windows**zaznacz pole wyboru **Internet Information Services (IIS)** na liście **składniki** . Następnie kliknij przycisk **Zakończ** , aby zamknąć kreatora.

### <a name="to-create-the-publishing-macro"></a>Aby utworzyć makro publikowania

1. Aby otworzyć Eksploratora makr, w menu **Narzędzia** wskaż polecenie **makra**, a następnie kliknij przycisk **Eksplorator makr**.

2. Utwórz nowy moduł makr. W Eksploratorze makr wybierz pozycję Moje **makra**. W menu **Narzędzia** wskaż polecenie **makra**, a następnie kliknij polecenie **Nowy moduł makr**. Nazwij moduł **PublishSpecificCulture**.

3. W Eksploratorze makr rozwiń węzeł moje **makra** , a następnie otwórz moduł **PublishAllProjects** , klikając go dwukrotnie (lub, w menu **Narzędzia** , wskaż polecenie **makra**, a następnie kliknij pozycję **makra środowiska IDE**).

4. W środowisku IDE makr Dodaj następujący kod do modułu, po `Import` instrukcji:

    ```vb
    Module PublishSpecificCulture
        Sub PublishProjectFirstProjectWithEnLocale()
            ' Note: You should publish projects by using the IDE at least once
            ' before you use this macro. Items such as the certificate and the
            ' security zone must be set.
            Dim localeString As String = "en"

            ' Get first project.
            Dim proj As Project = DTE.Solution.Projects.Item(1)
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value

            ' GenerateManifests and SignManifests must always be set to
            ' True for publishing to work.
            proj.Properties.Item("GenerateManifests").Value = True
            proj.Properties.Item("SignManifests").Value = True

            'Set the publish language.
            'This will set the deployment language and pick up all
            ' en resource dlls:
            Dim originalTargetCulture As String = _
                publishProperties.Item("TargetCulture").Value
            publishProperties.Item("TargetCulture").Value = localeString

            'Append 'en' to end of publish, install, and update URLs if needed:
            Dim originalPublishUrl As String = _
                publishProperties.Item("PublishUrl").Value
            Dim originalInstallUrl As String = _
                publishProperties.Item("InstallUrl").Value
            Dim originalUpdateUrl As String = _
                publishProperties.Item("UpdateUrl").Value
            publishProperties.Item("PublishUrl").Value = _
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))
            If originalInstallUrl <> String.Empty Then
                publishProperties.Item("InstallUrl").Value = _
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))
            End If
            If originalUpdateUrl <> String.Empty Then
                publishProperties.Item("UpdateUrl").Value = _
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))
            End If
            proj.Save()

            Dim slnbld2 As SolutionBuild2 = _
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)
            slnbld2.Clean(True)

            slnbld2.BuildProject( _
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _
            proj.UniqueName, True)

            ' Only publish if build is successful.
            If slnbld2.LastBuildInfo <> 0 Then
                MsgBox("Build failed for " & proj.UniqueName)
            Else
                slnbld2.PublishProject( _
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _
                proj.UniqueName, True)
                If slnbld2.LastPublishInfo = 0 Then
                    MsgBox("Publish succeeded for " & proj.UniqueName _
                    & vbCrLf & "." _
                    & " Publish Language was '" & localeString & "'.")
                Else
                    MsgBox("Publish failed for " & proj.UniqueName)
                End If
            End If

            ' Return URLs and target culture to their previous state.
            publishProperties.Item("PublishUrl").Value = originalPublishUrl
            publishProperties.Item("InstallUrl").Value = originalInstallUrl
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl
            publishProperties.Item("TargetCulture").Value = originalTargetCulture
            proj.Save()
        End Sub

        Private Function AppendStringToUrl(ByVal str As String, _
        ByVal baseUri As Uri) As String
            Dim returnValue As String = baseUri.OriginalString
            If baseUri.IsFile OrElse baseUri.IsUnc Then
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)
            Else
                If Not baseUri.ToString.EndsWith("/") Then
                    returnValue = baseUri.OriginalString & "/" & str
                Else
                    returnValue = baseUri.OriginalString & str
                End If
            End If
            Return returnValue
        End Function
    End Module
    ```

5. Zamknij środowisko IDE makr. Fokus powróci do programu Visual Studio.

### <a name="to-publish-a-project-for-a-specific-locale"></a>Aby opublikować projekt dla określonych ustawień regionalnych

1. Aby utworzyć Visual Basic projekt aplikacji systemu Windows, w menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

2. W oknie dialogowym **Nowy projekt** wybierz pozycję **aplikacja systemu Windows** z węzła **Visual Basic** . Nazwij projekt *PublishLocales*.

3. Kliknij przycisk Form1. W oknie **Właściwości** , w obszarze **projekt**, Zmień właściwość **Language** z **(domyślnie)** na **angielski**. Zmień właściwość **Text** **formularza na.**

     Należy pamiętać, że zlokalizowane biblioteki DLL zasobów nie są tworzone, dopóki nie są one używane. Na przykład, są tworzone podczas zmiany tekstu w formularzu lub jednej z jej kontrolek po określeniu nowych ustawień regionalnych.

4. Publikuj *PublishLocales* przy użyciu środowiska IDE programu Visual Studio.

     W **Eksplorator rozwiązań**wybierz pozycję *PublishLocales*. W menu **projekt** wybierz polecenie **Właściwości**. W projektancie projektu na stronie **Publikowanie** Określ lokalizację publikacji **http://localhost/PublishLocales** , a następnie kliknij pozycję **Opublikuj teraz**.

     Gdy zostanie wyświetlona strona publikowanie strony sieci Web, zamknij ją. (W tym kroku należy tylko opublikować projekt; nie trzeba go instalować).

5. Opublikuj ponownie *PublishLocales* , wywołując makro w oknie wiersza polecenia programu Visual Studio. Aby wyświetlić okno wiersza polecenia, w menu **Widok** wskaż polecenie **inne okna** , a następnie kliknij polecenie **okno polecenia**lub naciśnij **klawisze CTRL** + **Alt** + **A**. W oknie wiersza polecenia wpisz `macros` : funkcja autouzupełniania będzie dostarczać listę dostępnych makr. Wybierz Poniższe makro i naciśnij klawisz ENTER:

     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`

6. Po pomyślnym zakończeniu procesu publikowania zostanie wygenerowany komunikat "opublikowanie zakończyło się powodzeniem dla *PublishLocales\PublishLocales.vbproj*. Język publikacji to "pl". " Kliknij przycisk **OK** w oknie komunikatu. Gdy zostanie wyświetlona strona publikowanie strony sieci Web, kliknij przycisk **Instaluj**.

7. Szukaj w *C:\Inetpub\wwwroot\PublishLocales\en*. Oprócz zlokalizowanej biblioteki DLL zasobów powinny zostać wyświetlone zainstalowane pliki, takie jak manifesty, *setup.exe*i plik publikowania strony sieci Web. (Domyślnie Technologia ClickOnce dołącza rozszerzenie *. deploy* do exe i bibliotek dll; to rozszerzenie można usunąć po wdrożeniu).

## <a name="see-also"></a>Zobacz też
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Środowisko deweloperskie makr](/previous-versions/visualstudio/visual-studio-2010/fb30sxt3(v=vs.100))
- [Okno Eksploratora makr](/previous-versions/visualstudio/visual-studio-2010/wwkx67sw(v=vs.100))
- [Instrukcje: edytowanie i Programistyczne tworzenie makr](/previous-versions/visualstudio/visual-studio-2010/k91y6132(v=vs.100))