import { useState, useEffect } from "react";

export default function JapaneseClockWidget() {
  const [time, setTime] = useState(new Date());

  useEffect(() => {
    const timer = setInterval(() => setTime(new Date()), 1000);
    return () => clearInterval(timer);
  }, []);

  const formatTime = (date) => {
    return new Intl.DateTimeFormat("ja-JP", {
      hour: "2-digit",
      minute: "2-digit",
      second: "2-digit",
      hour12: false,
      timeZone: "Asia/Tokyo",
    }).format(date);
  };

  return (
    <div className="flex flex-col items-center p-4 bg-white rounded-2xl shadow-lg border border-gray-300 w-64">
      <h2 className="text-lg font-semibold mb-2">日本時間 (JST)</h2>
      <div className="text-3xl font-bold text-gray-800">{formatTime(time)}</div>
    </div>
  );
}
