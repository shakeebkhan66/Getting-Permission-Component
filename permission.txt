checkpermission_opencamera()async {
    PermissionStatus camerStatus = await Permission.camera.request();
    if (camerStatus == PermissionStatus.granted) {
      barCodeScanner();
      ScaffoldMessenger.of(context).showSnackBar(
          const SnackBar(content: Text("Permission Granted")));
    }
    if (camerStatus == PermissionStatus.denied) {
      ScaffoldMessenger.of(context).showSnackBar(const SnackBar(
          content: Text("You Need To Provide Camera Permission.")));
    }
    if (camerStatus == PermissionStatus.permanentlyDenied) {
      openAppSettings();
    }
  }
