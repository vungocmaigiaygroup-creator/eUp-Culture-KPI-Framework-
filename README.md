# eUp-Culture-KPI-Framework import { useState } from "react";
const COLORS = {
blue: "#0582ba",
yellow: "#f6bd01",
green: "#2e9d43",
indigo: "#587dbb",
blueDark: "#046a9a",
blueLight: "#e8f5fc",
yellowLight: "#fffbea",
greenLight: "#eaf7ec",
indigoLight: "#eef2fb",
gray: "#f4f6f8",
grayMid: "#e0e5ec",
textDark: "#1a2233",
textMid: "#4a5568",
textLight: "#8a97aa",
white: "#ffffff",
};
const VALUES = [
{
key: "tam_tam",
label: "Tận Tâm",
icon: " ",
color: COLORS.blue,
lightColor: COLORS.blueLight,
behaviors: [
"Hoàn thành công việc đúng thời hạn đã cam kết",
"Chủ động báo cáo khó khăn thay vì để ảnh hưởng tiến độ chung",
"Theo sát chất lượng công việc đến giai đoạn cuối cùng",
"Sẵn sàng hỗ trợ xử lý vấn đề phát sinh ngoài phạm vi công việc khi cần thiết",
],
},
{
key: "dong_doi",
label: "Đồng Đội",
icon: " ",
color: COLORS.green,
lightColor: COLORS.greenLight,
behaviors: [
"Chủ động hỗ trợ đồng nghiệp khi phát sinh áp lực công việc",
"Sẵn sàng chia sẻ thông tin và kinh nghiệm cho các thành viên khác",
"Hợp tác tích cực với các phòng ban liên quan",
"Tôn trọng khác biệt quan điểm trong quá trình phản biện",
],
},
{
key: "doi_moi",
label: "Đổi Mới",
icon: " ",
color: COLORS.yellow,
lightColor: COLORS.yellowLight,
behaviors: [
"Chủ động đề xuất cải tiến quy trình hoặc sản phẩm",
"Tích cực cập nhật công nghệ và phương pháp làm việc mới",
"Sẵn sàng thử nghiệm giải pháp khác biệt",
"Có tinh thần học hỏi sau các thử nghiệm chưa thành công",
],
},
];
const LEVELS = [
{ score: 1, label: "Chưa thể hiện", color: "#e74c3c", short: "1" },
{ score: 2, label: "Thể hiện khi được nhắc nhở", color: "#f39c12", short: "2" },
{ score: 3, label: "Chủ động thể hiện", color: COLORS.blue, short: "3" },
{ score: 4, label: "Nổi bật & lan tỏa", color: COLORS.green, short: "4" },
];
const EMPLOYEES = [
{ id: 1, name: "Nguyễn Minh Tuấn", dept: "Product", avatar: "T" },
{ id: 2, name: "Trần Thị Lan Anh", dept: "Marketing", avatar: "L" },
{ id: 3, name: "Lê Văn Hoàng", dept: "Tech", avatar: "H" },
];
const defaultScores = () => {
const s = {};
VALUES.forEach((v) => {
v.behaviors.forEach((_, i) => {
s[`${v.key}_${i}`] = 0;
});
});
return s;
};
// ─── SCREEN 1: Dashboard ────────────────────────────────────────────────────
function Dashboard({ onNavigate }) {
const stats = [
{ label: "Nhân sự đã đánh giá", value: "24/31", sub: "Kỳ Q2/2025", color: COLORS.blue },
{ label: "Điểm văn hóa TB", value: "3.2 / 4", sub: "Toàn công ty", color: COLORS.green },
{ label: "Tỷ trọng điểm văn hóa", value: "22%", sub: "Trong tổng KPI", color: COLORS.indi
{ label: "Hành vi nổi bật nhất", value: "Đồng Đội", sub: "Điểm TB 3.5", color: "#f39c12"
];
const deptData = [
{ dept: "Product", tam: 3.4, doi: 3.2, moi: 3.6, total: 3.4 },
{ dept: "Marketing", tam: 3.1, doi: 3.5, moi: 3.0, total: 3.2 },
{ dept: "Tech", tam: 3.6, doi: 3.3, moi: 3.7, total: 3.5 },
{ dept: "Design", tam: 3.0, doi: 3.1, moi: 2.9, total: 3.0 },
{ dept: "HR / OD", tam: 3.8, doi: 3.6, moi: 3.2, total: 3.5 },
];
return (
<div style={{ padding: "28px 32px", background: COLORS.gray, minHeight: "100vh" }}>
{/* Header */}
<div style={{ marginBottom: 28 }}>
<div style={{ display: "flex", alignItems: "center", gap: 12, marginBottom: 4 }}>
<div style={{
width: 36, height: 36, borderRadius: 10,
background: `linear-gradient(135deg, ${COLORS.blue}, ${COLORS.indigo})`,
display: "flex", alignItems: "center", justifyContent: "center",
color: "#fff", fontWeight: 800, fontSize: 16, letterSpacing: 1,
}}>e</div>
<span style={{ fontWeight: 800, fontSize: 20, color: COLORS.textDark, letterSpacing
eUp <span style={{ color: COLORS.blue }}>Culture KPI</span>
</span>
</div>
<p style={{ color: COLORS.textLight, fontSize: 13, marginLeft: 48 }}>
Hệ thống đánh giá hành vi văn hóa doanh nghiệp — Kỳ Q2 / 2025
</p>
</div>
{/* Nav Tabs */}
<NavTabs active="dashboard" onNavigate={onNavigate} />
{/* Stats Cards */}
<div style={{ display: "grid", gridTemplateColumns: "repeat(4, 1fr)", gap: 16, marginBo
{stats.map((s, i) => (
<div key={i} style={{
background: COLORS.white, borderRadius: 14, padding: "20px 22px",
boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
borderTop: `4px solid ${s.color}`,
}}>
</div>
))}
<div style={{ fontSize: 26, fontWeight: 800, color: s.color, marginBottom: 4 }}>{
<div style={{ fontSize: 13, fontWeight: 600, color: COLORS.textDark }}>{s.label}<
<div style={{ fontSize: 11, color: COLORS.textLight, marginTop: 2 }}>{s.sub}</div
</div>
{/* Main content */}
<div style={{ display: "grid", gridTemplateColumns: "1.6fr 1fr", gap: 20 }}>
{/* Dept table */}
<div style={{ background: COLORS.white, borderRadius: 14, padding: 24, boxShadow: "0
<h3 style={{ margin: "0 0 16px", fontSize: 15, fontWeight: 700, color: COLORS.textD
Điểm văn hóa theo phòng ban
</h3>
<table style={{ width: "100%", borderCollapse: "collapse", fontSize: 13 }}>
<thead>
<tr style={{ background: COLORS.gray }}>
{["Phòng ban", "Tận Tâm", "Đồng Đội", "Đổi Mới", "Tổng TB"].map((h, i) <th key={i} style={{
padding: "10px 14px", textAlign: i === 0 ? "left" : "center",
color: COLORS.textMid, fontWeight: 600, fontSize: 12,
borderBottom: `2px solid ${COLORS.grayMid}`,
}}>{h}</th>
=> (
))}
</tr>
</thead>
<tbody>
{deptData.map((row, ri) => (
<tr key={ri} style={{ borderBottom: `1px solid ${COLORS.grayMid}` }}>
<td style={{ padding: "11px 14px", fontWeight: 600, color: COLORS.textDark
{[row.tam, row.doi, row.moi].map((v, vi) => {
const c = [COLORS.blue, COLORS.green, "#f39c12"][vi];
return (
<td key={vi} style={{ padding: "11px 14px", textAlign: "center" }}>
<ScorePill value={v} color={c} />
</td>
);
})}
<td style={{ padding: "11px 14px", textAlign: "center" }}>
<span style={{
fontWeight: 800, fontSize: 14,
color: row.total >= 3.4 ? COLORS.green : row.total >= 3.0 ? COLORS.blue
}}>{row.total.toFixed(1)}</span>
</td>
</tr>
))}
</tbody>
</table>
</div>
{/* Right panel */}
<div style={{ display: "flex", flexDirection: "column", gap: 18 }}>
{/* Progress */}
<div style={{ background: COLORS.white, borderRadius: 14, padding: 22, boxShadow: "
<h3 style={{ margin: "0 0 14px", fontSize: 15, fontWeight: 700, color: COLORS.tex
Tiến độ đánh giá
</h3>
{[
{ name: "Tự đánh giá", pct: 90, color: COLORS.blue },
{ name: "Đồng nghiệp đánh giá", pct: 72, color: COLORS.indigo },
{ name: "Leader đánh giá", pct: 65, color: COLORS.green },
].map((p, i) => (
<div key={i} style={{ marginBottom: 12 }}>
<div style={{ display: "flex", justifyContent: "space-between", marginBottom:
<span style={{ fontSize: 13, color: COLORS.textMid }}>{p.name}</span>
<span style={{ fontSize: 13, fontWeight: 700, color: p.color }}>{p.pct}%</s
</div>
<div style={{ height: 8, background: COLORS.grayMid, borderRadius: 99 }}>
<div style={{ height: "100%", width: `${p.pct}%`, background: p.color, bord
</div>
</div>
))}
</div>
{/* CTA */}
<div style={{
background: `linear-gradient(135deg, ${COLORS.blue}, ${COLORS.indigo})`,
borderRadius: 14, padding: 22, color: "#fff",
}}>
<div style={{ fontSize: 14, fontWeight: 700, marginBottom: 6 }}> Bắt đầu <div style={{ fontSize: 12, opacity: 0.85, marginBottom: 14 }}>
Kỳ đánh giá Q2/2025 đang mở. Hạn nộp: <strong>30/06/2025</strong>
</div>
<button
onClick={() => onNavigate("form")}
style={{
background: COLORS.yellow, color: COLORS.textDark,
border: "none", borderRadius: 8, padding: "9px 18px",
fontWeight: 700, fontSize: 13, cursor: "pointer", width: "100%",
}}>
</button>
Điền phiếu đánh giá →
</div>
</div>
</div>
</div>
đánh g
);
}
// ─── SCREEN 2: Evaluation Form ───────────────────────────────────────────────
function EvaluationForm({ onNavigate }) {
const [scores, setScores] = useState(defaultScores());
const [employee, setEmployee] = useState(EMPLOYEES[0]);
const [evaluator, setEvaluator] = useState("self");
const [submitted, setSubmitted] = useState(false);
const [activeVal, setActiveVal] = useState(0);
const setScore = (key, val) => setScores((prev) => ({ ...prev, [key]: val }));
const totalScore = () => {
let sum = 0, count = 0;
VALUES.forEach((v) => {
v.behaviors.forEach((_, i) => {
const s = scores[`${v.key}_${i}`];
if (s > 0) { sum += s; count++; }
});
});
return count > 0 ? (sum / count).toFixed(2) : "—";
};
const valueAvg = (vKey) => {
const v = VALUES.find((x) => x.key === vKey);
let sum = 0, count = 0;
v.behaviors.forEach((_, i) => {
const s = scores[`${vKey}_${i}`];
if (s > 0) { sum += s; count++; }
});
return count > 0 ? (sum / count).toFixed(1) : "—";
};
if (submitted) {
return (
<div style={{ padding: "28px 32px", background: COLORS.gray, minHeight: "100vh" }}>
<NavTabs active="form" onNavigate={onNavigate} />
<div style={{
marginTop: 40, background: COLORS.white, borderRadius: 18, padding: "48px 32px",
textAlign: "center", maxWidth: 520, margin: "40px auto 0",
boxShadow: "0 4px 24px rgba(0,0,0,0.08)",
}}>
<div style={{ fontSize: 56, marginBottom: 12 }}> </div>
<h2 style={{ color: COLORS.green, marginBottom: 8 }}>Đã nộp thành công!</h2>
<p style={{ color: COLORS.textMid, fontSize: 14 }}>
Phiếu đánh giá cho <strong>{employee.name}</strong> đã được lưu vào hệ thống.
</p>
<div style={{
background: COLORS.greenLight, borderRadius: 10, padding: "14px 20px",
margin: "20px 0", display: "flex", justifyContent: "center", gap: 32,
}}>
<div style={{ textAlign: "center" }}>
<div style={{ fontSize: 24, fontWeight: 800, color: COLORS.green }}>{totalScore
<div style={{ fontSize: 11, color: COLORS.textLight }}>Điểm văn hóa TB</div>
</div>
{VALUES.map((v) => (
<div key={v.key} style={{ textAlign: "center" }}>
<div style={{ fontSize: 24, fontWeight: 800, color: v.color }}>{valueAvg(v.ke
<div style={{ fontSize: 11, color: COLORS.textLight }}>{v.label}</div>
</div>
))}
</div>
<button
onClick={() => { setSubmitted(false); setScores(defaultScores()); }}
style={{
background: COLORS.blue, color: "#fff", border: "none",
borderRadius: 9, padding: "11px 28px", fontWeight: 700, fontSize: 14, cursor: "
}}>
Đánh giá nhân sự khác
</button>
</div>
</div>
);
}
return (
<div style={{ padding: "28px 32px", background: COLORS.gray, minHeight: "100vh" }}>
<NavTabs active="form" onNavigate={onNavigate} />
<div style={{ display: "grid", gridTemplateColumns: "300px 1fr", gap: 22, marginTop: 4
{/* Left sidebar */}
<div style={{ display: "flex", flexDirection: "column", gap: 16 }}>
{/* Employee picker */}
<div style={{ background: COLORS.white, borderRadius: 14, padding: 20, boxShadow: "
<div style={{ fontSize: 12, fontWeight: 700, color: COLORS.textLight, marginBotto
Nhân sự được đánh giá
</div>
{EMPLOYEES.map((e) => (
<div
key={e.id}
onClick={() => setEmployee(e)}
style={{
display: "flex", alignItems: "center", gap: 10, padding: "10px 12px",
borderRadius: 10, cursor: "pointer", marginBottom: 6,
background: employee.id === e.id ? COLORS.blueLight : "transparent",
border: `2px solid ${employee.id === e.id ? COLORS.blue : "transparent"}`,
transition: "all .2s",
}}>
<div style={{
width: 36, height: 36, borderRadius: "50%",
background: COLORS.blue, color: "#fff",
display: "flex", alignItems: "center", justifyContent: "center",
fontWeight: 800, fontSize: 15,
}}>{e.avatar}</div>
<div>
<div style={{ fontWeight: 600, fontSize: 13, color: COLORS.textDark }}>{e.n
<div style={{ fontSize: 11, color: COLORS.textLight }}>{e.dept}</div>
</div>
</div>
))}
</div>
{/* Evaluator type */}
<div style={{ background: COLORS.white, borderRadius: 14, padding: 20, boxShadow: "
<div style={{ fontSize: 12, fontWeight: 700, color: COLORS.textLight, marginBotto
Vai trò người đánh giá
</div>
{[
{ val: "self", label: "Tự đánh giá", icon: " " },
{ val: "peer", label: "Đồng nghiệp đánh giá", icon: " { val: "leader", label: "Leader đánh giá", icon: " " },
" },
].map((opt) => (
<div
key={opt.val}
onClick={() => setEvaluator(opt.val)}
style={{
display: "flex", alignItems: "center", gap: 9, padding: "9px 12px",
borderRadius: 9, cursor: "pointer", marginBottom: 5,
background: evaluator === opt.val ? COLORS.blueLight : COLORS.gray,
border: `2px solid ${evaluator === opt.val ? COLORS.blue : "transparent"}`,
}}>
<span style={{ fontSize: 16 }}>{opt.icon}</span>
<span style={{ fontSize: 13, fontWeight: evaluator === opt.val ? 700 : {opt.label}
</span>
</div>
400, c
))}
</div>
{/* Score summary */}
<div style={{ background: `linear-gradient(135deg, ${COLORS.blue}, ${COLORS.indigo}
<div style={{ fontSize: 12, fontWeight: 700, opacity: 0.8, marginBottom: 12, text
Tổng kết điểm
</div>
{VALUES.map((v) => (
<div key={v.key} style={{ display: "flex", justifyContent: "space-between", mar
<span style={{ fontSize: 13 }}>{v.icon} {v.label}</span>
<span style={{ fontWeight: 800, color: COLORS.yellow }}>{valueAvg(v.key)}</sp
</div>
paddin
))}
<div style={{ borderTop: "1px solid rgba(255,255,255,0.3)", marginTop: 10, <span style={{ fontWeight: 700 }}>Điểm tổng</span>
<span style={{ fontSize: 18, fontWeight: 900, color: COLORS.yellow }}>{totalSco
</div>
</div>
</div>
{/* Form main */}
<div style={{ background: COLORS.white, borderRadius: 14, padding: 28, boxShadow: "0
<div style={{ display: "flex", justifyContent: "space-between", alignItems: "center
<div>
<h2 style={{ margin: 0, fontSize: 17, fontWeight: 800, color: COLORS.textDark }
Phiếu đánh giá hành vi văn hóa
</h2>
<p style={{ margin: "4px 0 0", fontSize: 13, color: COLORS.textLight }}>
Nhân sự: <strong style={{ color: COLORS.blue }}>{employee.name}</strong> · {e
</p>
</div>
<div style={{ display: "flex", gap: 8 }}>
{VALUES.map((v, i) => (
<button
key={v.key}
onClick={() => setActiveVal(i)}
style={{
padding: "7px 14px", borderRadius: 8, cursor: "pointer",
fontWeight: 700, fontSize: 12, border: "none",
background: activeVal === i ? v.color : COLORS.gray,
color: activeVal === i ? "#fff" : COLORS.textMid,
transition: "all .2s",
}}>{v.icon} {v.label}</button>
))}
</div>
</div>
{/* Level legend */}
<div style={{
display: "flex", gap: 8, marginBottom: 20, padding: "10px 14px",
background: COLORS.gray, borderRadius: 10, flexWrap: "wrap",
}}>
<span style={{ fontSize: 11, fontWeight: 700, color: COLORS.textLight, marginRigh
{LEVELS.map((l) => (
<div key={l.score} style={{ display: "flex", alignItems: "center", gap: 5 }}>
<div style={{ width: 20, height: 20, borderRadius: 5, background: l.color, di
<span style={{ fontSize: 11, color: COLORS.textMid }}>{l.label}</span>
</div>
))}
</div>
{/* Behavior rows */}
{VALUES[activeVal].behaviors.map((beh, bi) => {
const key = `${VALUES[activeVal].key}_${bi}`;
const curScore = scores[key];
const vColor = VALUES[activeVal].color;
return (
<div key={bi} style={{
display: "flex", alignItems: "center", gap: 16, padding: "14px 16px",
borderRadius: 10, marginBottom: 10,
background: curScore > 0 ? `${vColor}10` : COLORS.gray,
border: `1.5px solid ${curScore > 0 ? vColor + "40" : "transparent"}`,
transition: "all .2s",
}}>
<div style={{
width: 26, height: 26, borderRadius: "50%",
background: vColor, color: "#fff",
display: "flex", alignItems: "center", justifyContent: "center",
fontSize: 12, fontWeight: 800, flexShrink: 0,
}}>{bi + 1}</div>
<div style={{ flex: 1, fontSize: 13.5, color: COLORS.textDark, lineHeight: 1.
<div style={{ display: "flex", gap: 6, flexShrink: 0 }}>
{LEVELS.map((l) => (
<button
key={l.score}
onClick={() => setScore(key, l.score)}
title={l.label}
style={{
width: 34, height: 34, borderRadius: 8, cursor: "pointer",
fontWeight: 800, fontSize: 13, border: "2px solid",
borderColor: curScore === l.score ? l.color : COLORS.grayMid,
background: curScore === l.score ? l.color : COLORS.white,
color: curScore === l.score ? "#fff" : COLORS.textMid,
transition: "all .15s",
}}>{l.score}</button>
))}
</div>
</div>
);
})}
{/* Nav between values */}
<div style={{ display: "flex", justifyContent: "space-between", alignItems: "center
<button
onClick={() => setActiveVal(Math.max(0, activeVal - 1))}
disabled={activeVal === 0}
style={{
padding: "9px 20px", borderRadius: 9, border: "none", cursor: "pointer",
background: activeVal === 0 ? COLORS.grayMid : COLORS.gray,
color: COLORS.textMid, fontWeight: 600, fontSize: 13,
}}>← Quay lại</button>
{activeVal < VALUES.length - 1 ? (
<button
onClick={() => setActiveVal(activeVal + 1)}
style={{
padding: "9px 20px", borderRadius: 9, border: "none", cursor: "pointer",
background: VALUES[activeVal].color, color: "#fff", fontWeight: 700, }}>Tiếp theo →</button>
fontSi
) : (
<button
onClick={() => setSubmitted(true)}
style={{
padding: "11px 28px", borderRadius: 9, border: "none", cursor: "pointer",
background: COLORS.green, color: "#fff", fontWeight: 800, fontSize: 14,
}}>✓ Nộp phiếu đánh giá</button>
)}
</div>
</div>
</div>
</div>
);
}
// ─── SCREEN 3: Framework Overview ────────────────────────────────────────────
function Framework({ onNavigate }) {
return (
<div style={{ padding: "28px 32px", background: COLORS.gray, minHeight: "100vh" }}>
<NavTabs active="framework" onNavigate={onNavigate} />
{/* Title banner */}
<div style={{
background: `linear-gradient(135deg, ${COLORS.blue} 0%, ${COLORS.indigo} 100%)`,
borderRadius: 16, padding: "28px 32px", marginBottom: 24, color: "#fff",
position: "relative", overflow: "hidden",
}}>
<div style={{
position: "absolute", right: -20, top: -20,
width: 160, height: 160, borderRadius: "50%",
background: "rgba(255,255,255,0.07)",
margin
}} />
<div style={{ fontSize: 12, fontWeight: 700, opacity: 0.7, letterSpacing: 1.5, Culture KPI Framework
</div>
<h1 style={{ margin: "0 0 8px", fontSize: 22, fontWeight: 900 }}>
Bộ chỉ số hành vi văn hóa (CBI)
</h1>
<p style={{ margin: 0, opacity: 0.85, fontSize: 14, maxWidth: 560, lineHeight: Hệ thống chuẩn hóa hành vi văn hóa eUp, tích hợp trực tiếp vào quy trình review lươ
</p>
<div style={{ display: "flex", gap: 20, marginTop: 18 }}>
{[
1.6 }}
{ label: "Trọng số trong KPI", val: "22%", icon: " { label: "Số giá trị cốt lõi", val: "3", icon: " { label: "Tổng hành vi đo lường", val: "12", icon: " { label: "Mô hình đánh giá", val: "360°", icon: " " },
" },
" },
" },
].map((s, i) => (
<div key={i} style={{ background: "rgba(255,255,255,0.13)", borderRadius: 10, pad
<div style={{ fontSize: 18, marginBottom: 3 }}>{s.icon}</div>
<div style={{ fontWeight: 900, fontSize: 17 }}>{s.val}</div>
<div style={{ fontSize: 11, opacity: 0.75 }}>{s.label}</div>
</div>
))}
</div>
</div>
{/* Values grid */}
<div style={{ display: "grid", gridTemplateColumns: "repeat(3, 1fr)", gap: 18, marginBo
{VALUES.map((v) => (
<div key={v.key} style={{
background: COLORS.white, borderRadius: 14, overflow: "hidden",
boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
}}>
<div style={{ background: v.color, padding: "18px 22px", color: "#fff" }}>
<div style={{ fontSize: 28, marginBottom: 4 }}>{v.icon}</div>
<div style={{ fontWeight: 900, fontSize: 18 }}>{v.label}</div>
</div>
<div style={{ padding: "18px 22px" }}>
{v.behaviors.map((b, i) => (
<div key={i} style={{ display: "flex", alignItems: "flex-start", gap: 10, mar
<div style={{
width: 20, height: 20, borderRadius: "50%", flexShrink: 0, marginTop: 1,
background: v.lightColor, color: v.color,
display: "flex", alignItems: "center", justifyContent: "center",
fontSize: 10, fontWeight: 800,
}}>{i + 1}</div>
<div style={{ fontSize: 13, color: COLORS.textMid, lineHeight: 1.5 }}>{b}</
</div>
))}
</div>
</div>
))}
</div>
{/* Scale + 360 */}
<div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 18 }}>
{/* Scale */}
<div style={{ background: COLORS.white, borderRadius: 14, padding: 24, boxShadow: "0
<h3 style={{ margin: "0 0 16px", fontSize: 15, fontWeight: 700, color: COLORS.textD
Thang đánh giá 4 mức độ
</h3>
{LEVELS.map((l) => (
<div key={l.score} style={{
display: "flex", alignItems: "center", gap: 14, marginBottom: 12,
padding: "10px 14px", borderRadius: 10, background: COLORS.gray,
borderLeft: `4px solid ${l.color}`,
}}>
<div style={{
width: 30, height: 30, borderRadius: 8, background: l.color,
color: "#fff", display: "flex", alignItems: "center", justifyContent: "center
fontWeight: 900, fontSize: 15, flexShrink: 0,
}}>{l.score}</div>
<div>
<div style={{ fontWeight: 700, fontSize: 13, color: COLORS.textDark }}>{l.lab
</div>
</div>
))}
</div>
{/* 360 model */}
<div style={{ background: COLORS.white, borderRadius: 14, padding: 24, boxShadow: "0
<h3 style={{ margin: "0 0 16px", fontSize: 15, fontWeight: 700, color: COLORS.textD
Mô hình đánh giá 360°
</h3>
{[
{ who: "Nhân viên tự đánh giá", icon: " { who: "Đồng nghiệp đánh giá chéo", icon: " { who: "Leader trực tiếp đánh giá", icon: " ].map((r, i) => (
<div key={i} style={{
display: "flex", alignItems: "center", gap: 12, marginBottom: 12,
", color: COLORS.blue, pct: "33%" ", color: COLORS.indigo, pct: },
"33%"
", color: COLORS.green, pct: "34%" }
padding: "12px 16px", borderRadius: 10,
background: `${r.color}10`,
border: `1.5px solid ${r.color}30`,
}}>
<span style={{ fontSize: 22 }}>{r.icon}</span>
<div style={{ flex: 1 }}>
<div style={{ fontWeight: 600, fontSize: 13, color: COLORS.textDark }}>{r.who
</div>
<div style={{ fontWeight: 800, color: r.color, fontSize: 14 }}>{r.pct}</div>
</div>
))}
<div style={{
background: `${COLORS.yellow}25`, borderRadius: 10, padding: "12px 16px",
borderLeft: `4px solid ${COLORS.yellow}`, marginTop: 8,
}}>
<div style={{ fontSize: 12.5, color: COLORS.textMid, lineHeight: 1.5 }}>
<strong style={{ color: COLORS.textDark }}>Trọng số tổng:</strong> Điểm văn hóa
</div>
</div>
</div>
</div>
</div>
);
}
// ─── SCREEN 4: Roadmap ───────────────────────────────────────────────────────
function Roadmap({ onNavigate }) {
const phases = [
{
num: 1, range: "Tháng 1–2", title: "Xây dựng Framework",
color: COLORS.blue, icon: " ",
tasks: [
"Bộ phận OD phối hợp với lãnh đạo xây dựng bộ hành vi chuẩn",
"Xác định thang đo và trọng số phù hợp",
"Thiết kế biểu mẫu đánh giá tích hợp vào quy trình hiện có",
"Xây dựng tài liệu hướng dẫn nội bộ",
],
},
{
num: 2, range: "Tháng 3–4", title: "Thử nghiệm Nội bộ",
color: COLORS.indigo, icon: " ",
tasks: [
"Thí điểm tại Product, Marketing, Tech",
"Tổ chức workshop nội bộ giải thích framework mới",
"Đào tạo leader cách đưa feedback về hành vi văn hóa",
"Thu thập phản hồi, điều chỉnh bộ chỉ số",
],
},
{
num: 3, range: "Tháng 5–6", title: "Triển khai Toàn Doanh Nghiệp",
color: COLORS.green, icon: " ",
tasks: [
"Áp dụng đánh giá 360° toàn công ty",
"Tích hợp điểm văn hóa vào kỳ review lương",
"Ghi nhận và khen thưởng các cá nhân điểm nổi bật",
"Đánh giá hiệu quả và cập nhật framework định kỳ",
],
},
];
const kpis = [
{ label: "Tỷ lệ nhân sự hiểu rõ hành vi văn hóa cốt lõi", target: "≥ 90%", color: COLORS.
{ label: "Mức độ đồng nhất trong đánh giá giữa các leader", target: "Độ lệch < 0.5", colo
{ label: "Giảm phản hồi tiêu cực về tác phong & phối hợp", target: "−30%", color: COLORS.
{ label: "Mức độ gắn kết nội bộ (eNPS)", target: "+10 điểm", color: "#f39c12" },
{ label: "Nhân sự chủ động tham gia hoạt động văn hóa", target: "≥ 75%", color: COLORS.bl
];
return (
<div style={{ padding: "28px 32px", background: COLORS.gray, minHeight: "100vh" }}>
<NavTabs active="roadmap" onNavigate={onNavigate} />
<h2 style={{ margin: "0 0 20px", fontSize: 18, fontWeight: 800, color: COLORS.textDark
Lộ trình triển khai — 6 tháng
</h2>
positi
{/* Timeline */}
<div style={{ position: "relative", marginBottom: 28 }}>
<div style={{
position: "absolute", top: 28, left: 28, right: 28, height: 3,
background: COLORS.grayMid, zIndex: 0,
}} />
<div style={{ display: "grid", gridTemplateColumns: "repeat(3, 1fr)", gap: 18, {phases.map((p) => (
<div key={p.num} style={{ background: COLORS.white, borderRadius: 14, overflow: "
<div style={{ background: p.color, padding: "18px 22px", color: "#fff" }}>
<div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 6
<div style={{
width: 32, height: 32, borderRadius: "50%",
background: "rgba(255,255,255,0.2)",
display: "flex", alignItems: "center", justifyContent: "center",
fontWeight: 900, fontSize: 15,
}}>0{p.num}</div>
<span style={{ fontSize: 15, fontWeight: 900 }}>{p.title}</span>
</div>
<div style={{ fontSize: 13, opacity: 0.85 }}> {p.range}</div>
</div>
<div style={{ padding: "18px 22px" }}>
{p.tasks.map((t, i) => (
<div key={i} style={{ display: "flex", alignItems: "flex-start", gap: 8, ma
<div style={{
width: 6, height: 6, borderRadius: "50%",
background: p.color, marginTop: 6, flexShrink: 0,
}} />
<div style={{ fontSize: 13, color: COLORS.textMid, lineHeight: 1.5 </div>
}}>{t}
))}
</div>
</div>
))}
</div>
</div>
{/* KPIs */}
<div style={{ background: COLORS.white, borderRadius: 14, padding: 24, boxShadow: "0 2p
<h3 style={{ margin: "0 0 18px", fontSize: 15, fontWeight: 700, color: COLORS.textDar
Tiêu chí đánh giá hiệu quả
</h3>
<div style={{ display: "grid", gridTemplateColumns: "repeat(5, 1fr)", gap: 14 }}>
{kpis.map((k, i) => (
<div key={i} style={{
background: COLORS.gray, borderRadius: 12, padding: "16px 14px",
borderBottom: `3px solid ${k.color}`,
textAlign: "center",
}}>
</div>
<div style={{ fontSize: 22, fontWeight: 900, color: k.color, marginBottom: 8 }}
<div style={{ fontSize: 12, color: COLORS.textMid, lineHeight: 1.5 }}>{k.label}
))}
</div>
</div>
</div>
);
}
// ─── Helpers ─────────────────────────────────────────────────────────────────
function ScorePill({ value, color }) {
return (
<span style={{
display: "inline-block", padding: "3px 11px", borderRadius: 99,
background: `${color}15`, color: color,
fontWeight: 700, fontSize: 13,
}}>{value}</span>
);
}
function NavTabs({ active, onNavigate }) {
const tabs = [
{ id: "dashboard", label: " Dashboard" },
{ id: "framework", label: " { id: "form", label: " Framework" },
Phiếu đánh giá" },
{ id: "roadmap", label: " Lộ trình" },
];
return (
<div style={{ display: "flex", gap: 6, marginBottom: 22, background: COLORS.white, {tabs.map((t) => (
<button
key={t.id}
onClick={() => onNavigate(t.id)}
style={{
padding: "8px 18px", borderRadius: 9, border: "none", cursor: "pointer",
fontWeight: 700, fontSize: 13, transition: "all .2s",
background: active === t.id ? COLORS.blue : "transparent",
color: active === t.id ? "#fff" : COLORS.textMid,
}}>{t.label}</button>
paddin
))}
</div>
);
}
// ─── App Root ────────────────────────────────────────────────────────────────
export default function App() {
const [screen, setScreen] = useState("dashboard");
return (
<div style={{ fontFamily: "'Segoe UI', 'Helvetica Neue', Arial, sans-serif", minHeight: "
{screen === "dashboard" && <Dashboard onNavigate={setScreen} />}
{screen === "framework" && <Framework onNavigate={setScreen} />}
{screen === "form" && <EvaluationForm onNavigate={setScreen} />}
{screen === "roadmap" && <Roadmap onNavigate={setScreen} />}
</div>
);
}
