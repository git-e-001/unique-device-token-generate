# unique-device-token-generate


const generateDeviceFingerprint = () => {
  const userAgent = window.navigator.userAgent;
  const screenResolution = `${window.screen.width}x${window.screen.height}`;
  const colorDepth = window.screen.colorDepth;
  const timeZoneOffset = new Date().getTimezoneOffset();
  const plugins = Array.from(navigator.plugins)
    .map((plugin) => plugin.name)
    .join(", ");
  const fingerprint = `${userAgent}${screenResolution}${colorDepth}${timeZoneOffset}${plugins}`;
  const hashedFingerprint = calculateSHA256Hash(fingerprint);
  return hashedFingerprint;
};
