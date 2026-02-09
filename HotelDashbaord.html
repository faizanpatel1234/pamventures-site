import React, { useState, useEffect, useMemo } from 'react';
import { 
  PieChart, Pie, Cell, BarChart, Bar, XAxis, YAxis, CartesianGrid, Tooltip, Legend, ResponsiveContainer, AreaChart, Area
} from 'recharts';
import { 
  LayoutDashboard, Upload, DollarSign, TrendingUp, TrendingDown, 
  FileText, Plus, Trash2, Save, Download, Menu, X,
  ArrowUpRight, ArrowDownRight, Wallet, Activity
} from 'lucide-react';

// --- Utility Functions ---

const generateId = () => Math.random().toString(36).substr(2, 9);

const formatDate = (dateString) => {
  if (!dateString) return '';
  const date = new Date(dateString);
  return date.toLocaleDateString('en-US', { year: 'numeric', month: 'short', day: 'numeric' });
};

const formatCurrency = (amount) => {
  return new Intl.NumberFormat('en-IN', {
    style: 'currency',
    currency: 'INR',
    maximumFractionDigits: 0
  }).format(amount);
};

// --- Components ---

const Card = ({ children, className = "" }) => (
  <div className={`bg-white rounded-xl shadow-sm border border-slate-100 ${className}`}>
    {children}
  </div>
);

const StatCard = ({ title, value, type, trend }) => {
  const colorClass = type === 'income' ? 'text-emerald-600' : type === 'expense' ? 'text-rose-600' : 'text-blue-600';
  const bgClass = type === 'income' ? 'bg-emerald-50' : type === 'expense' ? 'bg-rose-50' : 'bg-blue-50';
  const icon = type === 'income' ? <TrendingUp size={24} /> : type === 'expense' ? <TrendingDown size={24} /> : <Wallet size={24} />;

  return (
    <div className="bg-white p-6 rounded-xl shadow-sm border border-slate-100 flex items-center justify-between transition-transform hover:scale-[1.02] duration-200">
      <div>
        <p className="text-sm font-medium text-slate-500 mb-1">{title}</p>
        <h3 className={`text-2xl font-bold ${colorClass}`}>{value}</h3>
        {trend && <p className="text-xs text-slate-400 mt-2">{trend}</p>}
      </div>
      <div className={`p-4 rounded-full ${bgClass} ${colorClass}`}>
        {icon}
      </div>
    </div>
  );
};

const TransactionTable = ({ data, onDelete }) => (
  <div className="overflow-x-auto">
    <table className="w-full text-left border-collapse">
      <thead>
        <tr className="bg-slate-50/50 text-slate-500 text-xs uppercase tracking-wider">
          <th className="p-4 font-semibold">Date</th>
          <th className="p-4 font-semibold">Description</th>
          <th className="p-4 font-semibold">Category</th>
          <th className="p-4 font-semibold text-right">Amount</th>
          {onDelete && <th className="p-4 font-semibold text-center">Action</th>}
        </tr>
      </thead>
      <tbody className="divide-y divide-slate-50">
        {data.map(t => (
          <tr key={t.id} className="hover:bg-slate-50 transition-colors group">
            <td className="p-4 text-slate-600 whitespace-nowrap text-sm">{formatDate(t.date)}</td>
            <td className="p-4 text-slate-800 font-medium text-sm">{t.description}</td>
            <td className="p-4">
              <span className="px-2.5 py-1 bg-slate-100 text-slate-600 rounded-full text-xs font-medium border border-slate-200">
                {t.category}
              </span>
            </td>
            <td className={`p-4 text-right font-bold text-sm ${t.type === 'income' ? 'text-emerald-600' : 'text-rose-600'}`}>
              {t.type === 'income' ? '+' : '-'}{formatCurrency(t.amount)}
            </td>
            {onDelete && (
              <td className="p-4 text-center">
                <button 
                  onClick={() => onDelete(t.id)} 
                  className="text-slate-300 hover:text-rose-500 transition-colors p-1"
                >
                  <Trash2 size={16} />
                </button>
              </td>
            )}
          </tr>
        ))}
        {data.length === 0 && (
          <tr>
            <td colSpan={onDelete ? 5 : 4} className="p-8 text-center text-slate-400">No records found</td>
          </tr>
        )}
      </tbody>
    </table>
  </div>
);

const CSVUploader = ({ onImport }) => {
  const [dragActive, setDragActive] = useState(false);
  const [file, setFile] = useState(null);
  const [preview, setPreview] = useState([]);
  const [headers, setHeaders] = useState([]);
  const [mapping, setMapping] = useState({
    date: '',
    description: '',
    amount: '',
    type: '',
    category: ''
  });

  const handleDrag = (e) => {
    e.preventDefault();
    e.stopPropagation();
    if (e.type === "dragenter" || e.type === "dragover") {
      setDragActive(true);
    } else if (e.type === "dragleave") {
      setDragActive(false);
    }
  };

  const handleDrop = (e) => {
    e.preventDefault();
    e.stopPropagation();
    setDragActive(false);
    if (e.dataTransfer.files && e.dataTransfer.files[0]) {
      handleFile(e.dataTransfer.files[0]);
    }
  };

  const handleChange = (e) => {
    if (e.target.files && e.target.files[0]) {
      handleFile(e.target.files[0]);
    }
  };

  const handleFile = (file) => {
    setFile(file);
    const reader = new FileReader();
    reader.onload = (e) => {
      const text = e.target.result;
      const lines = text.split('\n').map(line => line.trim()).filter(line => line);
      if (lines.length > 0) {
        const headers = lines[0].split(',').map(h => h.trim());
        setHeaders(headers);
        const previewData = lines.slice(1, 6).map(line => {
          const values = line.split(',');
          return headers.reduce((obj, header, index) => {
            obj[header] = values[index];
            return obj;
          }, {});
        });
        setPreview(previewData);
        
        const newMapping = { ...mapping };
        headers.forEach(h => {
          const lower = h.toLowerCase();
          if (lower.includes('date') || lower.includes('time')) newMapping.date = h;
          if (lower.includes('desc') || lower.includes('particular')) newMapping.description = h;
          if (lower.includes('amount') || lower.includes('total') || lower.includes('price')) newMapping.amount = h;
          if (lower.includes('type') || lower.includes('cr/dr')) newMapping.type = h;
          if (lower.includes('cat') || lower.includes('dept')) newMapping.category = h;
        });
        setMapping(newMapping);
      }
    };
    reader.readAsText(file);
  };

  const processImport = () => {
    if (!file) return;
    const reader = new FileReader();
    reader.onload = (e) => {
      const text = e.target.result;
      const lines = text.split('\n').map(line => line.trim()).filter(line => line);
      const headers = lines[0].split(',').map(h => h.trim());
      
      const newTransactions = lines.slice(1).map(line => {
        const values = line.split(','); 
        const row = headers.reduce((obj, header, index) => {
          obj[header] = values[index];
          return obj;
        }, {});

        let type = 'expense';
        let amount = parseFloat(row[mapping.amount] || 0);

        if (mapping.type) {
          const typeVal = row[mapping.type]?.toLowerCase() || '';
          if (typeVal.includes('income') || typeVal.includes('cr') || typeVal.includes('credit') || typeVal.includes('sale')) {
            type = 'income';
          }
        } else {
          const catVal = row[mapping.category]?.toLowerCase() || '';
          if (catVal.includes('room') || catVal.includes('f&b') || catVal.includes('sale') || catVal.includes('revenue')) {
            type = 'income';
          }
        }

        return {
          id: generateId(),
          date: row[mapping.date] ? new Date(row[mapping.date]).toISOString() : new Date().toISOString(),
          description: row[mapping.description] || 'Imported Transaction',
          amount: Math.abs(amount),
          type: type,
          category: row[mapping.category] || 'Uncategorized',
          source: 'Import'
        };
      }).filter(t => !isNaN(t.amount) && t.amount > 0);

      onImport(newTransactions);
      setFile(null);
      setPreview([]);
    };
    reader.readAsText(file);
  };

  return (
    <Card className="p-8">
      <div className="text-center mb-8">
        <h2 className="text-2xl font-bold text-slate-800">Import CSV Data</h2>
        <p className="text-slate-500">Upload your IDS Next or Bank Statement exports</p>
      </div>
      
      {!file ? (
        <div 
          className={`border-2 border-dashed rounded-2xl p-12 text-center transition-all duration-200 ${dragActive ? 'border-blue-500 bg-blue-50 scale-[1.01]' : 'border-slate-300 hover:border-slate-400 hover:bg-slate-50'}`}
          onDragEnter={handleDrag} 
          onDragLeave={handleDrag} 
          onDragOver={handleDrag} 
          onDrop={handleDrop}
        >
          <div className="bg-white p-4 rounded-full inline-block shadow-sm mb-4">
            <Upload className="h-8 w-8 text-blue-600" />
          </div>
          <p className="text-xl font-medium text-slate-700 mb-2">Drag & Drop file here</p>
          <p className="text-slate-500 mb-6">or</p>
          <input 
            type="file" 
            accept=".csv"
            className="hidden" 
            id="csv-upload" 
            onChange={handleChange}
          />
          <label htmlFor="csv-upload" className="inline-flex items-center justify-center px-6 py-3 border border-transparent text-base font-medium rounded-lg text-white bg-blue-600 hover:bg-blue-700 cursor-pointer shadow-sm hover:shadow-md transition-all">
            Browse Files
          </label>
        </div>
      ) : (
        <div className="space-y-6 animate-fadeIn">
          <div className="flex items-center justify-between bg-blue-50 p-4 rounded-lg border border-blue-100">
            <div className="flex items-center gap-3">
              <FileText className="text-blue-600" />
              <span className="font-medium text-blue-900">{file.name}</span>
            </div>
            <button onClick={() => setFile(null)} className="text-blue-400 hover:text-blue-600">
              <X size={20} />
            </button>
          </div>

          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
            {['Date', 'Description', 'Amount', 'Category'].map(field => (
              <div key={field}>
                <label className="block text-xs font-semibold uppercase tracking-wider text-slate-500 mb-1.5">{field} Column</label>
                <select 
                  className="w-full border-slate-200 rounded-lg shadow-sm focus:border-blue-500 focus:ring-blue-500 p-2.5 bg-white text-sm"
                  value={mapping[field.toLowerCase()]}
                  onChange={(e) => setMapping({...mapping, [field.toLowerCase()]: e.target.value})}
                >
                  <option value="">Select Column...</option>
                  {headers.map(h => <option key={h} value={h}>{h}</option>)}
                </select>
              </div>
            ))}
          </div>

          <div className="flex justify-end pt-4">
            <button 
              onClick={processImport}
              className="px-6 py-2.5 bg-blue-600 text-white rounded-lg hover:bg-blue-700 flex items-center gap-2 font-medium shadow-sm hover:shadow-md transition-all"
            >
              <Save size={18} />
              Confirm Import
            </button>
          </div>
        </div>
      )}
    </Card>
  );
};

// --- Main Application Component ---

const App = () => {
  const [activeTab, setActiveTab] = useState('overview');
  const [transactions, setTransactions] = useState([]);
  const [loading, setLoading] = useState(true);
  const [sidebarOpen, setSidebarOpen] = useState(false);
  const [showAddModal, setShowAddModal] = useState(false);

  const [newTx, setNewTx] = useState({
    date: new Date().toISOString().split('T')[0],
    description: '',
    amount: '',
    type: 'expense',
    category: 'Operational'
  });

  useEffect(() => {
    const saved = localStorage.getItem('hotel_finance_data');
    if (saved) {
      try { setTransactions(JSON.parse(saved)); } catch (e) { console.error(e); }
    } else {
      setTransactions([
        { id: '1', date: '2023-10-25', description: 'Room 101 Booking', amount: 4500, type: 'income', category: 'Room Revenue' },
        { id: '2', date: '2023-10-25', description: 'Vegetable Supply', amount: 1200, type: 'expense', category: 'F&B Cost' },
        { id: '3', date: '2023-10-26', description: 'Banquet Advance', amount: 15000, type: 'income', category: 'Banquet' },
        { id: '4', date: '2023-10-26', description: 'Electricity Bill', amount: 8500, type: 'expense', category: 'Utilities' },
      ]);
    }
    setLoading(false);
  }, []);

  useEffect(() => {
    if (!loading) localStorage.setItem('hotel_finance_data', JSON.stringify(transactions));
  }, [transactions, loading]);

  const handleImport = (newData) => {
    setTransactions(prev => [...prev, ...newData]);
    alert(`Successfully imported ${newData.length} records.`);
    setActiveTab('transactions');
  };

  const addTransaction = (e) => {
    e.preventDefault();
    if (!newTx.description || !newTx.amount) return;
    const transaction = {
      id: generateId(),
      ...newTx,
      amount: parseFloat(newTx.amount),
      date: new Date(newTx.date).toISOString()
    };
    setTransactions(prev => [transaction, ...prev]);
    setNewTx({ ...newTx, description: '', amount: '' });
    setShowAddModal(false);
  };

  const deleteTransaction = (id) => {
    if (window.confirm('Delete this record?')) {
      setTransactions(prev => prev.filter(t => t.id !== id));
    }
  };

  const handleExport = () => {
    const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(transactions));
    const downloadAnchorNode = document.createElement('a');
    downloadAnchorNode.setAttribute("href", dataStr);
    downloadAnchorNode.setAttribute("download", "hotel_finance_backup.json");
    document.body.appendChild(downloadAnchorNode);
    downloadAnchorNode.click();
    downloadAnchorNode.remove();
  };

  // --- Analytics Logic ---
  const stats = useMemo(() => {
    const totalIncome = transactions.filter(t => t.type === 'income').reduce((sum, t) => sum + t.amount, 0);
    const totalExpense = transactions.filter(t => t.type === 'expense').reduce((sum, t) => sum + t.amount, 0);
    const profit = totalIncome - totalExpense;

    const getCategoryData = (type) => {
      const grouped = transactions.filter(t => t.type === type).reduce((acc, t) => {
        acc[t.category] = (acc[t.category] || 0) + t.amount;
        return acc;
      }, {});
      return Object.keys(grouped).map(key => ({ name: key, value: grouped[key] }));
    };

    const getTrendData = () => {
      const last7Days = [...Array(7)].map((_, i) => {
        const d = new Date();
        d.setDate(d.getDate() - i);
        return d.toISOString().split('T')[0];
      }).reverse();

      return last7Days.map(date => {
        const dayData = transactions.filter(t => t.date.startsWith(date));
        return {
          date: new Date(date).toLocaleDateString('en-US', {weekday: 'short'}),
          income: dayData.filter(t => t.type === 'income').reduce((sum, t) => sum + t.amount, 0),
          expense: dayData.filter(t => t.type === 'expense').reduce((sum, t) => sum + t.amount, 0),
        };
      });
    };

    return { 
      totalIncome, 
      totalExpense, 
      profit, 
      incomeCategories: getCategoryData('income'),
      expenseCategories: getCategoryData('expense'),
      trendData: getTrendData() 
    };
  }, [transactions]);

  // --- Render Functions ---

  const renderOverview = () => (
    <div className="space-y-6 animate-fadeIn">
      <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
        <StatCard title="Total Income" value={formatCurrency(stats.totalIncome)} type="income" trend="All time" />
        <StatCard title="Total Expenses" value={formatCurrency(stats.totalExpense)} type="expense" trend="All time" />
        <StatCard title="Net Profit" value={formatCurrency(stats.profit)} type="profit" trend="All time" />
      </div>

      <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
        <Card className="col-span-1 lg:col-span-2 p-6">
          <h3 className="text-lg font-bold text-slate-800 mb-6 flex items-center gap-2">
            <Activity size={20} className="text-blue-500" />
            Financial Flow (Last 7 Days)
          </h3>
          <div className="h-72">
            <ResponsiveContainer width="100%" height="100%">
              <BarChart data={stats.trendData} barGap={8}>
                <CartesianGrid strokeDasharray="3 3" vertical={false} stroke="#f1f5f9" />
                <XAxis dataKey="date" axisLine={false} tickLine={false} tick={{fill: '#64748b', fontSize: 12}} dy={10} />
                <YAxis axisLine={false} tickLine={false} tick={{fill: '#64748b', fontSize: 12}} tickFormatter={(val) => `₹${val/1000}k`} />
                <Tooltip 
                  cursor={{fill: '#f8fafc'}}
                  contentStyle={{borderRadius: '8px', border: 'none', boxShadow: '0 4px 6px -1px rgb(0 0 0 / 0.1)'}}
                />
                <Legend iconType="circle" />
                <Bar dataKey="income" fill="#10b981" radius={[4, 4, 0, 0]} name="Income" barSize={32} />
                <Bar dataKey="expense" fill="#f43f5e" radius={[4, 4, 0, 0]} name="Expenses" barSize={32} />
              </BarChart>
            </ResponsiveContainer>
          </div>
        </Card>

        <Card className="p-6">
          <div className="flex justify-between items-center mb-6">
             <h3 className="text-lg font-bold text-slate-800">Recent Transactions</h3>
             <button onClick={() => setActiveTab('transactions')} className="text-blue-600 text-sm font-medium hover:underline">See all</button>
          </div>
          <div className="overflow-hidden">
             <TransactionTable data={transactions.slice(0, 5)} />
          </div>
        </Card>
      </div>
    </div>
  );

  const renderIncomeView = () => (
    <div className="space-y-6 animate-fadeIn">
      <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
        <StatCard title="Total Income" value={formatCurrency(stats.totalIncome)} type="income" trend="Revenue Generated" />
        <Card className="p-6">
          <h3 className="text-lg font-bold text-slate-800 mb-4">Income Sources</h3>
           <div className="h-48">
            <ResponsiveContainer width="100%" height="100%">
              <PieChart>
                <Pie
                  data={stats.incomeCategories}
                  cx="50%"
                  cy="50%"
                  innerRadius={50}
                  outerRadius={70}
                  paddingAngle={5}
                  dataKey="value"
                >
                  {stats.incomeCategories.map((entry, index) => (
                    <Cell key={`cell-${index}`} fill={['#10b981', '#3b82f6', '#8b5cf6', '#f59e0b'][index % 4]} />
                  ))}
                </Pie>
                <Tooltip formatter={(value) => formatCurrency(value)} />
                <Legend layout="vertical" verticalAlign="middle" align="right" />
              </PieChart>
            </ResponsiveContainer>
          </div>
        </Card>
      </div>

      <Card className="p-0 overflow-hidden">
        <div className="p-6 border-b border-slate-100">
           <h3 className="text-lg font-bold text-slate-800">Income History</h3>
        </div>
        <TransactionTable data={transactions.filter(t => t.type === 'income')} onDelete={deleteTransaction} />
      </Card>
    </div>
  );

  const renderExpenseView = () => (
    <div className="space-y-6 animate-fadeIn">
      <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
        <StatCard title="Total Expenses" value={formatCurrency(stats.totalExpense)} type="expense" trend="Cost Incurred" />
        <Card className="p-6">
          <h3 className="text-lg font-bold text-slate-800 mb-4">Expense Breakdown</h3>
           <div className="h-48">
            <ResponsiveContainer width="100%" height="100%">
              <PieChart>
                <Pie
                  data={stats.expenseCategories}
                  cx="50%"
                  cy="50%"
                  innerRadius={50}
                  outerRadius={70}
                  paddingAngle={5}
                  dataKey="value"
                >
                  {stats.expenseCategories.map((entry, index) => (
                    <Cell key={`cell-${index}`} fill={['#f43f5e', '#f59e0b', '#6366f1', '#ec4899'][index % 4]} />
                  ))}
                </Pie>
                <Tooltip formatter={(value) => formatCurrency(value)} />
                <Legend layout="vertical" verticalAlign="middle" align="right" />
              </PieChart>
            </ResponsiveContainer>
          </div>
        </Card>
      </div>

      <Card className="p-0 overflow-hidden">
        <div className="p-6 border-b border-slate-100">
           <h3 className="text-lg font-bold text-slate-800">Expense History</h3>
        </div>
        <TransactionTable data={transactions.filter(t => t.type === 'expense')} onDelete={deleteTransaction} />
      </Card>
    </div>
  );

  return (
    <div className="min-h-screen bg-slate-50 font-sans text-slate-900 flex">
      {/* Mobile Toggle */}
      <button 
        className="lg:hidden fixed bottom-6 right-6 z-50 bg-blue-600 text-white p-4 rounded-full shadow-lg hover:bg-blue-700 transition-all"
        onClick={() => setSidebarOpen(!sidebarOpen)}
      >
        {sidebarOpen ? <X size={24} /> : <Menu size={24} />}
      </button>

      {/* Sidebar */}
      <aside className={`
        fixed lg:static inset-y-0 left-0 z-40 w-72 bg-white border-r border-slate-200 transition-transform duration-300 transform 
        ${sidebarOpen ? 'translate-x-0' : '-translate-x-full lg:translate-x-0'}
      `}>
        <div className="p-8">
          <h1 className="text-2xl font-extrabold tracking-tight text-slate-900 flex items-center gap-2">
            <div className="w-8 h-8 bg-blue-600 rounded-lg flex items-center justify-center text-white">
              <Activity size={20} />
            </div>
            Hotel<span className="text-blue-600">Dash</span>
          </h1>
        </div>

        <nav className="px-4 space-y-1">
          <p className="px-4 text-xs font-semibold text-slate-400 uppercase tracking-wider mb-2 mt-4">Analytics</p>
          <button onClick={() => { setActiveTab('overview'); setSidebarOpen(false); }}
            className={`w-full flex items-center gap-3 px-4 py-3 rounded-xl transition-all font-medium ${activeTab === 'overview' ? 'bg-blue-50 text-blue-700' : 'text-slate-600 hover:bg-slate-50'}`}>
            <LayoutDashboard size={20} /> Overview
          </button>
          <button onClick={() => { setActiveTab('income'); setSidebarOpen(false); }}
            className={`w-full flex items-center gap-3 px-4 py-3 rounded-xl transition-all font-medium ${activeTab === 'income' ? 'bg-emerald-50 text-emerald-700' : 'text-slate-600 hover:bg-slate-50'}`}>
            <TrendingUp size={20} /> Income
          </button>
          <button onClick={() => { setActiveTab('expenses'); setSidebarOpen(false); }}
            className={`w-full flex items-center gap-3 px-4 py-3 rounded-xl transition-all font-medium ${activeTab === 'expenses' ? 'bg-rose-50 text-rose-700' : 'text-slate-600 hover:bg-slate-50'}`}>
            <TrendingDown size={20} /> Expenses
          </button>

          <p className="px-4 text-xs font-semibold text-slate-400 uppercase tracking-wider mb-2 mt-8">Management</p>
          <button onClick={() => { setActiveTab('transactions'); setSidebarOpen(false); }}
            className={`w-full flex items-center gap-3 px-4 py-3 rounded-xl transition-all font-medium ${activeTab === 'transactions' ? 'bg-blue-50 text-blue-700' : 'text-slate-600 hover:bg-slate-50'}`}>
            <FileText size={20} /> All Transactions
          </button>
          <button onClick={() => { setActiveTab('import'); setSidebarOpen(false); }}
            className={`w-full flex items-center gap-3 px-4 py-3 rounded-xl transition-all font-medium ${activeTab === 'import' ? 'bg-blue-50 text-blue-700' : 'text-slate-600 hover:bg-slate-50'}`}>
            <Upload size={20} /> Import Data
          </button>
        </nav>
      </aside>

      {/* Main Content */}
      <main className="flex-1 p-4 lg:p-10 overflow-y-auto h-screen bg-slate-50/50">
        <div className="max-w-7xl mx-auto">
          <header className="flex flex-col md:flex-row md:items-center justify-between gap-4 mb-8">
            <div>
              <h2 className="text-3xl font-bold text-slate-900 capitalize">
                {activeTab}
              </h2>
              <p className="text-slate-500 mt-1">
                {new Date().toLocaleDateString('en-US', { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' })}
              </p>
            </div>
            
            <div className="flex gap-3">
               <button 
                onClick={() => setShowAddModal(!showAddModal)}
                className="flex items-center gap-2 px-5 py-2.5 bg-blue-600 text-white rounded-xl hover:bg-blue-700 shadow-lg shadow-blue-200 transition-all font-medium"
              >
                <Plus size={20} />
                <span className="hidden md:inline">Quick Add</span>
              </button>
              <button onClick={handleExport} className="flex items-center gap-2 px-4 py-2.5 bg-white border border-slate-200 text-slate-700 rounded-xl hover:bg-slate-50 font-medium">
                 <Download size={20} />
              </button>
            </div>
          </header>

          {/* Quick Add Modal Area */}
          {showAddModal && (
            <div className="mb-8 animate-fadeIn">
               <Card className="p-6 border-blue-100 ring-4 ring-blue-50">
                <div className="flex justify-between items-center mb-4">
                  <h3 className="text-lg font-bold text-slate-800">Add New Entry</h3>
                  <button onClick={() => setShowAddModal(false)}><X className="text-slate-400" /></button>
                </div>
                <form onSubmit={addTransaction} className="grid grid-cols-1 md:grid-cols-5 gap-4 items-end">
                  <div className="md:col-span-1">
                    <label className="block text-xs font-semibold uppercase text-slate-500 mb-1">Date</label>
                    <input type="date" required className="w-full border-slate-200 rounded-lg p-2.5" value={newTx.date} onChange={e => setNewTx({...newTx, date: e.target.value})} />
                  </div>
                  <div className="md:col-span-1">
                    <label className="block text-xs font-semibold uppercase text-slate-500 mb-1">Type</label>
                    <select className="w-full border-slate-200 rounded-lg p-2.5" value={newTx.type} onChange={e => setNewTx({...newTx, type: e.target.value})}>
                      <option value="income">Income</option>
                      <option value="expense">Expense</option>
                    </select>
                  </div>
                  <div className="md:col-span-1">
                    <label className="block text-xs font-semibold uppercase text-slate-500 mb-1">Description</label>
                    <input type="text" required placeholder="Description" className="w-full border-slate-200 rounded-lg p-2.5" value={newTx.description} onChange={e => setNewTx({...newTx, description: e.target.value})} />
                  </div>
                  <div className="md:col-span-1">
                    <label className="block text-xs font-semibold uppercase text-slate-500 mb-1">Amount</label>
                    <input type="number" required placeholder="0.00" className="w-full border-slate-200 rounded-lg p-2.5" value={newTx.amount} onChange={e => setNewTx({...newTx, amount: e.target.value})} />
                  </div>
                  <div className="md:col-span-1">
                     <button type="submit" className="w-full bg-slate-900 text-white p-2.5 rounded-lg hover:bg-slate-800 transition-colors">Save</button>
                  </div>
                </form>
               </Card>
            </div>
          )}

          {activeTab === 'overview' && renderOverview()}
          {activeTab === 'income' && renderIncomeView()}
          {activeTab === 'expenses' && renderExpenseView()}
          
          {activeTab === 'transactions' && (
             <Card className="p-0 overflow-hidden">
                <div className="p-6 border-b border-slate-100 flex justify-between items-center">
                   <h3 className="text-lg font-bold text-slate-800">All Transactions</h3>
                </div>
                <TransactionTable data={transactions} onDelete={deleteTransaction} />
             </Card>
          )}

          {activeTab === 'import' && <CSVUploader onImport={handleImport} />}
        </div>
      </main>
    </div>
  );
};

export default App;
